# OpenCore-M11G-6900XT

OpenCore configuration for ASUS ROG MAXIMUS XI GENE and helper script to create EFI directory.

Table of Contents
Hardware list
macOS
OpenCore
Known Issues
ACPI
USB
Drivers
Kext
Resources
Tools
BIOS Settings
Installation
Download EFI folder archive from repository releases page
Create EFI directory and files helper script
Hardware list
Original hardware selection idea is based on tonymacx86.com Stork's MyHero II Build

Type	Item
Motherboard	Asus ROG MAXIMUS XI GENE ATX LGA1151 Motherboard
CPU	Intel - Core i9-9900K 3.6 GHz 8-Core Processor
CPU Cooler	NZXT X73 with NOCTUA F12 industrialPPC-2000 PWM
Thermal paste	ARCTIC MX-4 2019 Edition 4 g Thermal Paste
Memory	Ballistix Sport LT 64G DDR4, 2400 MHz CL16, BLS4C16G4D240FSB
Video Card	Sapphire Radeon RX 580 8 GB PULSE Video Card
Wi-Fi + Bluetooth Adapter PCI-E x1 Card	Fenvi HB1200 WiFi + Bluetooth 4.0 BCM4360
HDD 1,2	Samsung 860 Evo 500 GB 2.5" Solid State Drive
HDD 3	Seagate Barracuda 6 TB 3.5" 5400RPM Internal Hard Drive
Firewire	SYBA Low Profile PCI-Express Firewire Card
Power Supply	Corsair RMx (2018) 750 W 80+ Gold Certified Fully Modular ATX Power Supply
Case	Corsair 450D ATX Mid Tower Case
Monitor	Dell S2415H 23.8" 1920x1080 60 Hz Monitor
Camera	Logitech C920S HD Pro Webcam
Other accessories:

Type	Item
Keyboard	Magic Keyboard with Numeric Keypad
Trackpad	Magic Trackpad 2
macOS
macOS Big Sur version 11.3 (20E232) with FileVault 2 enabled.

You may find great installation guide here.

OpenCore
OpenCore 0.6.8
Dortania OpenCore Install Guide
OpenCore Configuration Sanity Checker
Known issues
Open: None.

Resolved:

 Fenvi T-919 WiFi + Bluetooth 4.0 BCM94360CD started having issues mid-autumn 2020:

After shut down and then powering on PC again, Bluetooth will not work when logged in to macOS. However, it's fine at earlier stages, e.g. when typing password during the boot. Workaround: unplug and plug power cord after the shutdown.
Keyboard and trackpad were working unstable from time to time (input garbage, freezes). Workaround: power cycle keyboard and trackpad, reboot.
Solution: (06-Dec-2020) Replaced Fenvi T-919 WiFi + Bluetooth 4.0 BCM94360CD with Fenvi HB1200 WiFi + Bluetooth 4.0 BCM4360.

 macOS Catalina version 10.15.7 started rebooting suddenly

MemTest86 revealed one BLS16G4D240FSB UDIMM to be faulty. Workaround: Remove faulty UDIMM.
Solution: (30-Nov-2020) Ordered and replaced faulty UDIMM.

ACPI
As per Dortania OpenCore Install Guide, compiled SSDTs:

SSDT-AWAC.aml
SSDT-EC-USBX.aml
SSDT-PLUG.aml
SSDT-PMC.aml
USB
Based on Dortania USB Mapping Guide and Intel USB mapping.

USB port naming is taken from this great reddit post. USB port mapping

Resulting USBMap.kext is used.

Drivers
OpenCore - OpenCanopy.efi, OpenRuntime.efi
OcBinaryData - HfsPlus.efi
Kext
AppleALC 1.5.9
IntelMausi 1.0.5
Lilu 1.5.2
VirtualSMC 1.2.2 (SMCProcessor.kext, SMCSuperIO.kext)
WhateverGreen 1.4.9
Resources
OcBinaryData - Resources/
Tools
OpenCore - CleanNvram.efi OpenControl.efi, OpenShell.efi
BIOS Settings
BIOS:

Version 1802 from download page.
Settings backup.
BIOS settings are based on Dortania Coffee Lake Intel BIOS settings recommendations:

Advanced

Submenu	Key: Value	Comment
CPU Configuration	Software Guard Extensions (SGX): Disabled	
CPU Configuration	Intel (VMX) Virtualization Technology: Enabled	Required for Docker
System Agent (SA) Configuration	VT-d: Enabled	could be enabled as DisableIoMapper is set to true
System Agent (SA) Configuration	Above 4G Decoding: Enabled	
USB Configuration	XHCI Hand-off: Enabled	
USB Configuration	Legacy USB Support: Enabled	
Boot

Submenu	Key: Value	Comment
Boot Configuration	Fast Boot: Disabled	
Boot Configuration	Boot Logo Display: Disabled	
Boot Configuration	Bootup NumLock State: Off	This is a matter of personal preferences
Secure Boot	OS Type: Windows UEFI mode	Ensure Secure Boot state is in Disabled state. If this is not the case, navigate to Boot -> Secure Boot -> Key Management and select Clear Secure Boot Keys
Installation
Build Status Latest ReleaseRelease date

There are two options to create EFI folder:

Download EFI folder archive from repository releases page
Create EFI directory and files with helper script
Download EFI folder archive from repository releases page
Navigate to repository releases page and download tarball or zip package.
Unarchive downloaded file locally
Replace {{SERIAL}}, {{BOARDSERIAL}} and {{SMUUID}} with actual values in EFI/OC/config.plist. If you don't have one, great example on how to do this could be found here.
Replace {{MACADDRESS}} with actual en0 MAC address value in EFI/OC/config.plist. Another great example on how to do it is here.
Once done, mount EFI partition and copy EFI folder there.
Create EFI directory and files with helper script
Requirements:

Bash > 4.0
Coreutils > 8.15
OpenSSL 1.1 (required for Wget)
Wget
Should you use Homebrew on macOS, install it with

brew install bash coreutils openssl@1.1 wget
To create EFI folder, there's no need to clone this repository, just run

bash -c "$(curl -fsSL raw.githubusercontent.com/vovinacci/OpenCore-ASUS-ROG-MAXIMUS-XI-HERO/master/create-efi.sh)"
This should download all necessary packages and extract files to the EFI folder in the current directory.

Two things to be done manually before moving everything to actual EFI partition:

Replace {{SERIAL}}, {{BOARDSERIAL}} and {{SMUUID}} with actual values in EFI/OC/config.plist. If you don't have one, great example on how to do this could be found here.
Replace {{MACADDRESS}} with actual en0 MAC address value in EFI/OC/config.plist. Another great example on how to do it is here.
After that, mount EFI partition and copy EFI folder there.
