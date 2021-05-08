# OpenCore-ASUS-ROG-MAXIMUS-XI-GENE

OpenCore configuration for ASUS ROG MAXIMUS XI HEROGENE and helper script to create EFI directory.

## Table of Contents

- [Hardware list](#hardware-list)
- [macOS](#macos)
- [OpenCore](#opencore)
  - [Known Issues](#known-issues)
  - [ACPI](#acpi)
  - [USB](#usb)
  - [Drivers](#drivers)
  - [Kext](#kext)
  - [Resources](#resources)
  - [Tools](#tools)
- [BIOS Settings](#bios-settings)
- [Installation](#installation)
  - [Download EFI folder archive from repository releases page](#download-efi-folder-archive-from-repository-releases-page)

## Hardware list


| Type | Item |
| ---- | ---- |
| Motherboard | [Asus ROG MAXIMUS XI GENE M-ATX LGA1151 Motherboard](https://pcpartpicker.com/product/Bmzkcf/asus-rog-maximus-xi-gene-micro-atx-lga1151-motherboard-rog-maximus-xi-gene) |
| CPU | [Intel - Core i9-9900K 3.6 GHz 8-Core Processor OC at 5.0Ghz](https://pcpartpicker.com/product/jHZFf7/intel-core-i9-9900k-36ghz-8-core-processor-bx80684i99900k) |
| CPU Cooler | [NZXT X73 Liquid CPU Cooler](https://pcpartpicker.com/product/F2rmP6/corsair-h60-2018-572-cfm-liquid-cpu-cooler-cw-9060036-ww) |
| Thermal paste | [Thermal Grizzly Kryonaut 5.5 g Thermal Paste](https://pcpartpicker.com/product/CRkwrH/thermal-grizzly-thermal-paste-tgk015r) |
| Memory | [Corsair Vengeance RGB Pro 64 GB (2 x 32 GB) DDR4-3600 CL18 Memory OC at 4000](https://pcpartpicker.com/product/LPK2FT/corsair-vengeance-rgb-pro-64-gb-2-x-32-gb-ddr4-3600-memory-cmw64gx4m2d3600c18) |
| Video Card | [AMD RADEON RX 6900 XT 7nm AMD RDNA2 16GB GDDR6 Video Card](https://item.jd.com/100009629167.html#crumb-wrap) |
| Wired Network Adapter  PCI-E x1 Card | [Asus XG-C100C PCIe x4 10 Gbit/s Network Adapter](https://pcpartpicker.com/product/7z4NnQ/asus-xg-c100c-network-adapter-xg-c100c) |
| NVME Solid State Drive 1 | [Samsung 970 Pro 1 TB M.2-2280 NVME Solid State Drive](https://pcpartpicker.com/product/g6Nv6h/samsung-970-pro-10tb-m2-2280-solid-state-drive-mz-v7p1t0bw) |
| NVME Solid State Drive 2 | [Western Digital SN750 1 TB M.2-2280 NVME Solid State Drive](https://pcpartpicker.com/product/QQrmP6/western-digital-sn750-1-tb-m2-2280-solid-state-drive-wds100t3x0c) |
| Power Supply | [Corsair RMx 750 W 80+ Gold Certified Fully Modular ATX Power Supply](https://pcpartpicker.com/product/9q38TW/corsair-power-supply-cp9020092na) |
| Case | [Phanteks Enthoo EVOLV TG MicroATX Mini Tower Case](https://pcpartpicker.com/product/mwbkcf/phanteks-enthoo-evolv-tg-silver-atx-mini-tower-case-ph-es314etg_gs) |
| Monitor | [BenQ PD2700U 27.0" 3840x2160 60 Hz Monitor](https://pcpartpicker.com/product/Gkkj4D/benq-pd2700u-270-3840x2160-60-hz-monitor-pd2700u) |
| Cooler Fans | [Noctua F12 industrialPPC-2000 PWM 71.69 CFM 120 mm Fan X3](https://pcpartpicker.com/product/NcQypg/noctua-case-fan-nff12industrialppc2000pwm) |
| Case Fans | [Noctua A14 PWM 82.5 CFM 140 mm Fan X2](https://pcpartpicker.com/product/dwR48d/noctua-case-fan-nfa14pwm) |

Other accessories:

| Type | Item |
| ---- | ---- |
| Keyboard | [Logitech G913 TKL RGB Wireless Gaming Keyboard](https://pcpartpicker.com/product/zCPgXL/logitech-g915-tkl-rgb-wireless-gaming-keyboard-920-009512) |
| Mouse | [Logitech G603 Wireless Optical Mouse](https://pcpartpicker.com/product/HgdFf7/logitech-g603-wireless-optical-mouse-910-005099) |

## macOS

macOS Big Sur version 11.4 beta (20F5055C).

You may find great installation guide [here](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/).

## OpenCore

- [OpenCore 0.6.9](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.6.9)
- [Dortania OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [OpenCore Configuration Sanity Checker](https://opencore.slowgeek.com/)

### Known issues


**WiFi + Bluetooth**:

- [x] [itlwm.kext]https://github.com/OpenIntelWireless/itlwm) 
- [x] [IntelBluetoothFirmware.kext]https://github.com/OpenIntelWireless/IntelBluetoothFirmware
- [ ] You can use this kexts drive your Intel WiFi & Bluetooth Card

  

### ACPI

As per [Dortania OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#acpi), compiled SSDTs:

- [SSDT-AWAC.aml](ACPI/SSDT-AWAC.aml)
- [SSDT-EC-USBX.aml](ACPI/SSDT-EC-USBX.aml)
- [SSDT-PLUG.aml](ACPI/SSDT-PLUG.aml)
- [SSDT-PMC.aml](ACPI/SSDT-PMC.aml)

### USB

Based on Dortania [USB Mapping Guide](https://dortania.github.io/OpenCore-Post-Install/usb/) and [Intel USB mapping](https://dortania.github.io/OpenCore-Post-Install/usb/intel-mapping/intel.html).


### Drivers

- OpenCore - `OpenCanopy.efi`, `OpenRuntime.efi`
- [OcBinaryData](https://github.com/acidanthera/OcBinaryData) - [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)

### Kext

- [AppleALC 1.6.0](https://github.com/acidanthera/AppleALC/releases/tag/1.6.0)
- [IntelMausi 1.0.6](https://github.com/acidanthera/IntelMausi/releases/tag/1.0.6)
- [Lilu 1.5.3](https://github.com/acidanthera/Lilu/releases/tag/1.5.3)
- [VirtualSMC 1.2.3](https://github.com/acidanthera/VirtualSMC/releases/tag/1.2.3) (`SMCProcessor.kext`, `SMCSuperIO.kext`)
- [WhateverGreen 1.4.9](https://github.com/acidanthera/WhateverGreen/releases/tag/1.4.9)

### Resources

- [OcBinaryData](https://github.com/acidanthera/OcBinaryData) - [Resources/](https://github.com/acidanthera/OcBinaryData/blob/master/Resources)

### Tools

- OpenCore - `ResetSystem.efi` `OpenControl.efi`, `OpenShell.efi`

## BIOS Settings

BIOS:

- Version [1602](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1151/ROG_MAXIMUS_XI_GENE/ROG-MAXIMUS-XI-GENE-ASUS-1602.zip) from [download page](https://rog.asus.com/motherboards/rog-maximus/rog-maximus-xi-gene-model/helpdesk_bios).
- Settings [backup](BIOS/V1602.CMO).

BIOS settings are based on Dortania [Coffee Lake Intel BIOS settings](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings) recommendations:
- First

  In the main screen, set X.M.P. to Enabled

- Advanced

  | Submenu | Key: Value | Comment |
  | --- | --- | --- |
  | CPU Configuration | Intel (VMX) Virtualization Technology > Enabled | Absolutely Required for [Parallels](https://www.parallels.com/) |
  | System Agent (SA) Configuration | VT-d > Enabled | |
  | System Agent (SA) Configuration | Above 4G Decoding > Enabled | |
  | System Agent (SA) Graphics Configuration | Primary Display > PCI for DGPU | |
  | System Agent (SA) Graphics Configuration | IGPU Multi-Monitor > Enabled for DGPU | |
  | System Agent (SA) Graphics Configuration | RC6(Render Standby) > Off | |
  | System Agent (SA) Graphics Configuration | DVMT Pre-Allocated > 128 | |
  | USB Configuration | XHCI Hand-off > Enabled | |
  | USB Configuration | Legacy USB Support > Disabled| |

- Boot

  | Submenu | Key: Value | Comment |
  | --- | --- | --- |
  | Boot Configuration | Fast Boot > Disabled| |
  | Boot Configuration | Boot Logo Display > Disabled| |
  | Boot Configuration | Post Report > 1 Sec | More secs if you need |
  | Boot Configuration | Setup Mode > Advanced | |
  | Secure Boot | OS Type: `Windows UEFI mode` | Ensure `Secure Boot state` is in `Disabled` state. If this is not the case, navigate to `Boot` -> `Secure Boot` -> `Key Management` and select `Clear Secure Boot Keys` |

## Installation

Create `EFI` folder:

- Download `EFI` folder archive from repository [releases page](https://github.com/sumisumu/OpenCore-M11G-6900XT/releases)

### Download EFI folder archive from repository releases page

- Navigate to repository [releases page](https://github.com/sumisumu/OpenCore-M11G-6900XT/releases) and download tarball or zip package.
- Unarchive downloaded file locally
- Replace `{{SERIAL}}`, `{{BOARDSERIAL}}` and `{{SMUUID}}` with actual values in `EFI/OC/config.plist`. If you don't have one, great example on how to do this could be found [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial).
- Replace `{{MACADDRESS}}` with actual `en0` MAC address value in `EFI/OC/config.plist`. Another great example on how to do it is [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#fixing-en0).
- Once done, mount EFI partition and copy `EFI` folder there.

### Create EFI directory and files 
Youtube：[sumi](https://www.youtube.com/channel/UCGDi2q78i2qQ6HF99wjmRyw)



