# MAGI Preliminary IP and VLAN Plan

This document defines the preliminary VLAN, IPv4 addressing, switch-port, and
inter-VLAN trust design for the MAGI Infrastructure project.

It builds on the physical and logical design described in
[`docs/hardware/initial-architecture.md`](../hardware/initial-architecture.md)
and the hardware recorded in
[`docs/hardware/inventory.md`](../hardware/inventory.md).

This plan is preliminary. Values may change during implementation, and the
decisions listed under [Deferred Decisions](#deferred-decisions) are
intentionally left open.

## Design Constraints

- MELCHIOR has one onboard Ethernet interface and uses a router-on-a-stick
  design. The WAN-side network and all internal VLANs share a single IEEE
  802.1Q trunk to the SG2210P.
- The ISP gateway connects to the SG2210P rather than directly to MELCHIOR, so
  the WAN-side network is carried on a dedicated WAN-TRANSIT VLAN.
- BALTHASAR, CASPER, DOGMA, ADAM, and LILITH each have a single Ethernet
  interface.
- The TP-Link Omada SG2210P provides 8 Gigabit PoE+ RJ-45 ports and 2 SFP
  slots.
- The design must remain simple enough for a single administrator to manage.

## Design Principles

- One `/24` subnet per internal VLAN.
- The third octet of each internal subnet matches the VLAN ID.
- The gateway for every internal VLAN is `.1` on MELCHIOR.
- All routing between VLANs is performed by MELCHIOR.
- The SG2210P operates at Layer 2 and has an IP address only on the
  management VLAN.
- Traffic between VLANs is denied by default and allowed only by explicit
  firewall rules.
- VLAN 1 is not used for MAGI traffic or switch management.

## VLANs

| VLAN ID | Name | Purpose | Status |
| --- | --- | --- | --- |
| 10 | MGMT | Firewall, switch, Proxmox host, and DOGMA management | Active initially |
| 20 | INFRA | Infrastructure servers and VMs: DNS, directory services, Linux infrastructure, SIEM | Active initially |
| 30 | CLIENTS | Wi-Fi access point and everyday client devices | Active initially |
| 40 | AI | GEHIRN | Reserved only; not created during initial deployment |
| 50 | IOT | IoT and PoE devices such as cameras or sensors | Reserved only; not created during initial deployment |
| 66 | PENTEST | Isolated penetration-testing and intentionally vulnerable systems | Active initially |
| 100 | WAN-TRANSIT | ISP gateway to MELCHIOR WAN interface only | Active initially |
| 999 | PARKING | Unused native VLAN / PVID for MELCHIOR's trunk and unused ports; no subnet or gateway, never routed | Active initially |

## IPv4 Subnets and Gateways

| VLAN | Subnet | Gateway | DHCP Pool |
| --- | --- | --- | --- |
| 10 MGMT | `10.10.10.0/24` | `10.10.10.1` | None, or a small recovery pool `.200–.209` |
| 20 INFRA | `10.10.20.0/24` | `10.10.20.1` | `.100–.199` (most hosts static) |
| 30 CLIENTS | `10.10.30.0/24` | `10.10.30.1` | `.100–.199` |
| 40 AI (reserved) | `10.10.40.0/24` | `10.10.40.1` | Static only |
| 50 IOT (reserved) | `10.10.50.0/24` | `10.10.50.1` | `.100–.199` |
| 66 PENTEST | `10.10.66.0/24` | `10.10.66.1` | `.100–.199` |
| 100 WAN-TRANSIT | ISP-assigned | ISP-assigned | Provided by ISP gateway |
| 999 PARKING | None | None | None |

### Address Layout Within Each Subnet

| Range | Use |
| --- | --- |
| `.1` | MELCHIOR gateway interface |
| `.2–.9` | Network equipment |
| `.10–.99` | Static hosts and VMs |
| `.100–.199` | DHCP clients |
| `.200–.254` | Reserved |

The `10.10.0.0/16` range was chosen to avoid overlapping with common ISP
gateway LAN ranges such as `192.168.0.0/24` and `192.168.1.0/24`, and to leave
room for future internal networks such as a VPN subnet.

## System Placement

| System | VLAN | Address |
| --- | --- | --- |
| MELCHIOR (management interface) | 10 MGMT | `10.10.10.1` (also `.1` on each active internal VLAN; ISP-assigned on WAN-TRANSIT) |
| TP-Link Omada SG2210P (management) | 10 MGMT | `10.10.10.2` |
| BALTHASAR (Proxmox host) | 10 MGMT | `10.10.10.11` |
| CASPER (Proxmox host) | 10 MGMT | `10.10.10.12` |
| DOGMA | 10 MGMT | `10.10.10.13` |
| ADAM (primary Pi-hole / DNS) | 20 INFRA | `10.10.20.11` |
| LILITH (secondary Pi-hole / DNS) | 20 INFRA | `10.10.20.12` |
| Infrastructure VMs (directory services, Linux, SIEM) | 20 INFRA | `10.10.20.20–.99` |
| Wi-Fi access point | 30 CLIENTS | `10.10.30.2` |
| Client devices | 30 CLIENTS | DHCP |
| GEHIRN (future) | 40 AI (reserved) | `10.10.40.11` |
| Penetration-testing and target VMs | 66 PENTEST | DHCP or static `.10–.99` |

### Placement Notes

- ADAM and LILITH are placed in INFRA rather than MGMT because they provide DNS
  to every VLAN. They are administered over SSH from MGMT.
- The Proxmox host management addresses for BALTHASAR and CASPER are in MGMT.
  Their virtual machines are placed in INFRA or PENTEST by VLAN tag on a
  VLAN-aware Proxmox bridge (for example `vmbr0`).
- Penetration-testing VMs should run primarily on CASPER, the
  security-services host, to keep them separate from BALTHASAR's
  infrastructure workloads.

## Switch Port Plan (SG2210P)

| Port | Connected Device | Mode | Untagged / PVID | Tagged VLANs | PoE |
| --- | --- | --- | --- | --- | --- |
| 1 | MELCHIOR | Trunk | 999 (PARKING, unused) | 10, 20, 30, 66, 100 | Off |
| 2 | ISP gateway | Access | 100 | — | Off |
| 3 | BALTHASAR | Hybrid / trunk | 10 | 20, 66 | Off |
| 4 | CASPER | Hybrid / trunk | 10 | 20, 66 | Off |
| 5 | DOGMA | Access | 10 | — | Off |
| 6 | ADAM | Access | 20 | — | PoE+ on |
| 7 | LILITH | Access | 20 | — | PoE+ on |
| 8 | Wi-Fi access point | Access | 30 | — | As needed |
| SFP 1–2 | Unused | — | 999 (PARKING) | — | — |

### Switch Port Notes

- **Port 1 (MELCHIOR):** VLANs 40 and 50 are added to the tagged list only
  when those VLANs are activated.
- **Port 2 (ISP gateway):** VLAN 100 (WAN-TRANSIT) must be present only on
  port 1 and port 2.
- **Ports 3 and 4 (BALTHASAR and CASPER):** VLAN 10 is intentionally
  untagged/native so Proxmox host management does not depend on tagged VLAN
  configuration. This keeps the hosts reachable for recovery even if the
  Proxmox VLAN configuration is incorrect. VM networks use tagged VLANs through
  a VLAN-aware Proxmox bridge. Because untagged traffic on these ports lands in
  MGMT, every VM network interface should be assigned an explicit VLAN tag.
  VLAN 40 may be added to BALTHASAR later if required.
- **Port 8 (Wi-Fi access point):** access VLAN 30 initially. It may become a
  trunk later if a VLAN-aware multi-SSID access point is used.
- **SFP 1–2:** unused, assigned to PARKING VLAN 999, and administratively
  disabled.
- ADAM and LILITH are the only planned PoE+ loads. The exact PoE budget should
  be confirmed against the SG2210P datasheet.

## Default Trust and Inter-VLAN Rules

All inter-VLAN routing and filtering is performed by MELCHIOR.

Trust order, from most to least trusted:

**MGMT > INFRA > AI > CLIENTS > IOT > PENTEST**

The baseline policy is to deny all traffic between VLANs and allow only the
flows listed below. The MELCHIOR web interface and SSH are reachable only from
MGMT.

### MGMT Access Model

MGMT follows a least-privilege model. It is not granted unrestricted access to
every VLAN. MGMT may reach only the administrative and monitoring services
required for each destination, such as SSH, HTTPS management interfaces, the
Proxmox web interface, and SNMP or health-check polling.

A temporary broad MGMT allow rule may be used during initial deployment or
troubleshooting and must be removed afterward.

### Inter-VLAN Matrix

| Source | To MGMT | To INFRA | To CLIENTS | To AI | To IOT | To PENTEST | To Internet |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MGMT | — | Required admin / monitoring services only | Required admin / monitoring services only | Required admin / monitoring services only | Required admin / monitoring services only | Deny (use Proxmox console) | Allow |
| INFRA | Deny | — | Deny | Deny | Deny | Deny | Allow |
| CLIENTS | Deny | DNS to ADAM and LILITH only ¹ | — | Deny | Deny | Deny | Allow |
| AI | Deny | Specific ports only (SIEM / log API) | Deny | — | Deny | Deny | Allow (may be tightened) |
| IOT | Deny | DNS only | Deny | Deny | — | Deny | Allow |
| PENTEST | Deny | Deny | Deny | Deny | Deny | — | Deny by default ² |
| WAN-TRANSIT | Deny | Deny | Deny | Deny | Deny | Deny | — |

¹ CLIENTS → INFRA remains default-deny with only explicitly required services.
Initially this is DNS to ADAM and LILITH. Active Directory services may be
added later if domain-joined clients are deployed.

² A disabled-by-default rule allowing PENTEST to reach the Internet may be
enabled temporarily for tool updates.

The AI and IOT rows apply only once VLANs 40 and 50 are activated.

### Additional Rules

- Every VLAN except PENTEST may reach ADAM and LILITH on TCP/UDP port 53. DHCP
  provides ADAM as the primary DNS server and LILITH as the secondary.
- Hosts in any VLAN except PENTEST may send logs or agent traffic to the SIEM
  VM in INFRA on the specific ports required.
- DOGMA performs SNMP, SSH, and health-check polling from MGMT using only the
  monitoring services allowed by the MGMT access model.
- PENTEST receives DHCP and DNS from MELCHIOR's own services only and cannot
  query ADAM or LILITH.
- Non-MGMT VLANs may reach MELCHIOR's interface addresses only for DHCP, DNS,
  and NTP.
- No inbound traffic from WAN-TRANSIT is allowed, except a future VPN service
  once remote access is designed.

## Deferred Decisions

The following decisions are intentionally left open:

- **Firewall platform:** pfSense or OPNsense. The rules in this document are
  platform-neutral.
- **ISP gateway mode:** bridge/passthrough mode versus double NAT. This
  affects MELCHIOR's addressing on WAN-TRANSIT VLAN 100.
- **Wi-Fi access point:** existing router in AP mode (access port in VLAN 30)
  versus a VLAN-aware multi-SSID access point (port 8 becomes a trunk).
- **Switch port capacity:** all 8 copper ports are assigned. GEHIRN, a wired
  administrator port, or a port-mirroring / IDS sensor port will require an
  SFP-to-RJ-45 module or an additional switch.
- **AI VLAN 40 activation and GEHIRN placement:** VLAN 40 is reserved. Exact
  flows to SIEM and log sources will be defined once GEHIRN's software stack is
  known.
- **IOT VLAN 50 activation:** created only if IoT or PoE devices are added.
- **Remote administration and jump-host design:** including a remote-access
  VPN (for example WireGuard or OpenVPN), its subnet, which VLANs VPN users may
  reach, and whether an administrator workstation or jump host is used to
  reach MGMT.
- **Active Directory access from CLIENTS:** added only if domain-joined clients
  are deployed.
- **Separate security/SIEM VLAN:** SIEM remains in INFRA initially and may be
  split out later if log volume or trust requirements justify it.
- **Pi-hole upstream resolver:** MELCHIOR's resolver versus a public resolver,
  and whether to use DNSSEC or DNS-over-TLS.
- **IPv6:** disabled or blocked initially; to be planned later.
- **NTP source, internal DNS domain** (for example `magi.home.arpa`), and
  integration between directory-services DNS and Pi-hole.
- **Bootstrap and migration order:** how MELCHIOR and the switch trunk will be
  configured without losing management access, such as keeping a temporary
  access port in VLAN 10 during setup.
