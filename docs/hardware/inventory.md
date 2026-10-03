# MAGI Hardware Inventory

This document records the physical hardware currently available for the
MAGI Infrastructure homelab.

Hardware is documented before operating systems are removed or major
configuration changes are made.

## MELCHIOR

**Status:** Inspected and operational

| Component | Information |
| --- | --- |
| Manufacturer | Dell |
| Model | OptiPlex 3070 Micro |
| Form Factor | Micro |
| Processor | Intel Core i5-9500T @ 2.20 GHz |
| CPU Cores / Threads | 6 / 6 |
| Memory | 16 GB DDR4 |
| Memory Configuration | 2 × 8 GB, dual channel |
| Memory Speed | 2666 MHz |
| Storage | 120 GB PNY SATA SSD |
| M.2 Storage Slot | PCIe M.2 slot empty |
| Ethernet | 1 onboard Ethernet port |
| Wireless | Qualcomm Wi-Fi adapter installed |
| Bluetooth | Installed |
| BIOS Version | 1.4.4 |
| Intel VT-x | Enabled |
| Intel VT-d | Enabled |
| Current Operating System | Proxmox VE |
| Current OS Access | Pre-existing installation; credentials unknown |
| Condition | Powers on and boots successfully; no visible damage, missing covers, or broken ports observed |
| Known Limitations / Issues | Small 120 GB system drive; only one onboard Ethernet interface; shared pool of two Dell power adapters across three OptiPlex systems |
| Preliminary Role | MAGI firewall / router |

MELCHIOR is planned to provide the firewall and routing functions for MAGI.

Because the system has only one onboard Ethernet interface, the preliminary
firewall design will require VLAN trunking and a router-on-a-stick style
configuration through the managed switch rather than separate physical WAN
and LAN interfaces.

The final firewall platform will be either pfSense or OPNsense and will be
selected before implementation.

---

## BALTHASAR

**Status:** Inspected; operational with BIOS/RTC warning

| Component | Information |
| --- | --- |
| Manufacturer | Dell |
| Model | OptiPlex 3070 Micro |
| Form Factor | Micro |
| Processor | Intel Core i5-9500T @ 2.20 GHz |
| CPU Cores / Threads | 6 / 6 |
| Memory | 16 GB DDR4 |
| Memory Configuration | 2 × 8 GB, dual channel |
| Memory Speed | 2400 MHz |
| Storage | 250 GB SATA drive + 256 GB M.2 PCIe SSD |
| Ethernet | 1 onboard Ethernet port |
| Wireless | Qualcomm Wi-Fi adapter installed |
| Bluetooth | Installed |
| BIOS Version | 1.7.1 |
| Intel VT-x | Enabled |
| Intel VT-d | Enabled |
| Current Operating System | Proxmox VE |
| Current OS Access | Pre-existing installation; credentials unknown |
| Condition | Powers on and boots successfully; no visible damage observed |
| Known Limitations / Issues | BIOS reports time-of-day not set and invalid configuration information; system clock reset to an incorrect date, suggesting the RTC/CMOS battery may need replacement |
| Preliminary Role | Primary Proxmox virtualization host |

BALTHASAR is planned as the primary Proxmox virtualization host for MAGI.

The system will provide capacity for infrastructure virtual machines and
services. The BIOS/RTC issue should be addressed before the system is placed
into regular service.

---

## CASPER

**Status:** Inspected and operational

| Component | Information |
| --- | --- |
| Manufacturer | Dell |
| Model | OptiPlex 3070 Micro |
| Form Factor | Micro |
| Processor | Intel Core i5-9500T @ 2.20 GHz |
| CPU Cores / Threads | 6 / 6 |
| Memory | 16 GB DDR4 |
| Memory Configuration | 2 × 8 GB, dual channel |
| Memory Speed | 2133 MHz |
| Storage | 250 GB SATA drive + 256 GB M.2 PCIe SSD |
| Ethernet | 1 onboard Ethernet port |
| Wireless | Qualcomm Wi-Fi adapter installed |
| Bluetooth | Installed |
| BIOS Version | 1.7.1 |
| Intel VT-x | Enabled |
| Intel VT-d | Enabled |
| Current Operating System | Proxmox VE |
| Current OS Access | Pre-existing installation; credentials unknown |
| Condition | Powers on and boots successfully; no visible damage observed |
| Known Limitations / Issues | None identified during initial inspection |
| Preliminary Role | Secondary Proxmox virtualization / security-services host |

CASPER is planned to provide additional virtualization capacity and host
security-related or infrastructure services.

Its exact virtual-machine and service assignments will be determined during
the infrastructure and monitoring design phases.

---

## DOGMA

**Status:** Operational; inspection partially complete

| Component | Information |
| --- | --- |
| Manufacturer | 10ZiG |
| Model / Series | 6000q Series |
| Form Factor | Thin client |
| Processor | TBD |
| CPU Cores / Threads | TBD |
| Memory | TBD |
| Storage | BIWIN Industrial mSATA drive; capacity TBD |
| Ethernet | 1 RJ-45 Ethernet port |
| USB | 4 rear USB-A + 2 front USB-A |
| Display Outputs | 2 DisplayPort |
| Audio | Front headphone and microphone jacks |
| BIOS Version | TBD |
| Virtualization Support | TBD |
| Boot Mode | UEFI |
| Bootloader | GNU GRUB 2.06-13+pmx2 |
| UEFI Boot Manager | Accessible |
| UEFI Setup Utility | Password-protected; credentials unknown |
| Current Operating System | Proxmox VE |
| Condition | Powers on and boots successfully into Proxmox VE; no obvious external damage or broken ports observed |
| Known Limitations / Issues | UEFI Setup Utility is password-protected; credentials unknown |
| Preliminary Role | Dedicated management and monitoring node |

DOGMA is planned for lightweight administrative and monitoring functions.

Possible responsibilities include secure remote administration, dashboards,
SNMP monitoring, health checks, and small administrative or automation
scripts.

---

# Raspberry Pi Systems

## ADAM

**Status:** Acquired

| Component | Information |
| --- | --- |
| Model | Raspberry Pi 5 |
| Memory | 16 GB |
| Ethernet | 1 Gigabit Ethernet port |
| Cooling | Raspberry Pi Active Cooler |
| Current Storage | TBD |
| Planned Power Method | PoE+ through managed PoE switch |
| Preliminary Role | Primary Pi-hole / DNS node |

ADAM is planned as the primary Pi-hole and DNS system for MAGI.

A combined PoE+ / NVMe HAT is planned so that the system can receive power
through Ethernet while retaining the option to use NVMe storage later.

ADAM can initially operate using microSD storage without an NVMe drive.

---

## LILITH

**Status:** Acquired

| Component | Information |
| --- | --- |
| Model | Raspberry Pi 5 |
| Memory | 16 GB |
| Ethernet | 1 Gigabit Ethernet port |
| Cooling | Raspberry Pi Active Cooler |
| Current Storage | TBD |
| Planned Power Method | PoE+ through managed PoE switch |
| Preliminary Role | Secondary Pi-hole / DNS node |

LILITH is planned as the secondary Pi-hole and DNS system for MAGI.

The secondary system is intended to maintain DNS availability if ADAM is
offline for maintenance or otherwise unavailable.

A combined PoE+ / NVMe HAT is planned so that LILITH can also receive power
through Ethernet and support future NVMe storage.

---

# Network Hardware

## TP-Link Omada SG2210P

**Status:** Acquired

| Component | Information |
| --- | --- |
| Manufacturer | TP-Link |
| Product Family | Omada |
| Model | SG2210P |
| Type | 10-Port Gigabit PoE+ Managed Switch |
| Managed | Yes |
| PoE | PoE+ |
| Preliminary Role | Central managed network switch for MAGI |

The SG2210P will serve as the central physical network connection point for
MAGI.

The switch will support VLAN-based segmentation, trunking, port-based VLAN
assignment, network monitoring, and PoE+ power for compatible devices such as
ADAM and LILITH.

Detailed VLAN and port configuration will be defined as part of the MAGI
network design.

---

# Rack Hardware

## DeskPi RackMate T1

**Status:** Acquired

| Component | Information |
| --- | --- |
| Manufacturer | DeskPi |
| Product | RackMate T1 |
| Rack Width | 10-inch |
| Rack Capacity | 8U |
| Preliminary Use | Physical mounting and organization of MAGI infrastructure |

The RackMate T1 will provide the primary physical enclosure for the MAGI
systems and networking equipment.

Final rack placement, shelves, patch-panel equipment, and cable-management
accessories will be documented as the physical installation is completed.

---

# Shared Hardware

## Dell Power Adapters

Two Dell power adapters are currently available for the three OptiPlex
systems.

This means all three OptiPlex systems cannot currently be powered
independently at the same time.

One additional compatible Dell power adapter is planned.

## 10ZiG Power Adapter

One dedicated 10ZiG power adapter is available for DOGMA.

## Raspberry Pi Accessories

The following Raspberry Pi accessories are currently available:

- 2 × Raspberry Pi Active Cooler
- 2 × Raspberry Pi M.2 HAT+

The separate M.2 HAT+ boards are not currently planned for the final ADAM
and LILITH configuration because combined PoE+ / NVMe HATs are planned
instead.

The M.2 HAT+ boards will be retained as spare hardware or may be used for
future Raspberry Pi expansion.

---

# Planned Hardware

## Combined Raspberry Pi PoE+ / NVMe HATs

**Status:** Planned / not yet acquired

**Quantity:** 2

**Planned Use:** PoE+ power and optional future NVMe storage for ADAM and
LILITH.

The HATs will allow both Raspberry Pi systems to receive network connectivity
and electrical power through the managed PoE+ switch.

NVMe drives are not currently required and may be added later.

## Additional Dell Power Adapter

**Status:** Planned / not yet acquired

**Quantity:** 1

**Planned Use:** Allow all three OptiPlex systems to operate simultaneously.

## GEHIRN

**Status:** Planned / future expansion

**Hardware:** GPU workstation using a repurposed NVIDIA RTX 3080 Ti

**Possible Use:** Local AI and security operations node

GEHIRN is planned to provide local AI services for tasks such as security
alert analysis, log analysis, reporting, and administrative assistance.

Final system specifications will be documented when the workstation is built.