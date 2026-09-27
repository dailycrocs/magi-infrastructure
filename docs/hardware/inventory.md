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
| Known Limitations / Issues | Small 120 GB system drive; shared pool of two Dell power adapters across three OptiPlex systems |
| Possible Use | Network security / sensor node |
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
| Possible Use | Primary Proxmox virtualization host |
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
| Possible Use | Secondary Proxmox virtualization / security services host |
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
| Possible Use | Dedicated management and monitoring node |
---

# Shared Hardware

## Dell Power Adapters

Two Dell power adapters are currently available for the three OptiPlex systems.

This means all three OptiPlex systems cannot be powered independently at the
same time without obtaining another compatible adapter.

## 10ZiG Power Adapter

One dedicated 10ZiG power adapter is available for DOGMA.

---

# Planned Hardware

## Raspberry Pi 5 Systems

**Status:** Planned / not yet acquired

**Quantity:** 2

**Preliminary Roles:**
- ADAM — Primary Pi-hole / DNS
- LILITH — Secondary Pi-hole / DNS

PoE+ HATs are also being considered so the Raspberry Pi systems can be
powered through the managed PoE switch.

Final hardware specifications will be documented after the devices are acquired.

## Dedicated Firewall Appliance

**Status:** Planned / not yet acquired

**Possible Use:** Dedicated pfSense or OPNsense firewall/router

The firewall appliance is planned to include multiple physical Ethernet
interfaces so that WAN and LAN connections can remain physically separated.

Final hardware specifications and firewall platform selection are still TBD.

## Managed PoE Switch

**Status:** Planned / not yet acquired

**Possible Use:** Central managed network switch for MAGI

The switch is planned to support Gigabit Ethernet, 802.1Q VLANs, trunking,
port-based VLAN assignment, PoE/PoE+, network monitoring, and future
infrastructure expansion.

A specific switch model has not yet been selected.

## GEHIRN

**Status:** Planned / future expansion

**Hardware:** GPU workstation using a repurposed NVIDIA RTX 3080 Ti

**Possible Use:** Local AI and security operations node

GEHIRN is planned to provide local AI services for tasks such as security
alert analysis, log analysis, reporting, and administrative assistance.

Final system specifications will be documented when the workstation is built.
