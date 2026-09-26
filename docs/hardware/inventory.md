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
| Possible Use | TBD |

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
| Possible Use | TBD |

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
| Possible Use | TBD |

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
| Possible Use | TBD |

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

## Raspberry Pi

**Status:** Planned / not yet acquired

**Possible Use:** Pi-hole / DNS filtering

Final hardware details will be documented after the device is acquired.