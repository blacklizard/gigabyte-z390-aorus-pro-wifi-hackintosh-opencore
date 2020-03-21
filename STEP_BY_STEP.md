# Step By Step Installation Guide for Catalina >=10.15.2

## BIOS Settings

BIOS version: `F11`

- Load Optimized Defaults
- Settings -> Internal Graphics -> Enabled
- Settings -> DVMT Pre-Allocated -> 32M
- Settings -> Wi-Fi -> Disabled
- Settings -> Above 4G Decoding -> Enabled
- Settings -> Wake on LAN Enable -> Disabled
- Settings -> USB Configuration -> Legacy USB Support -> Disabled
- Settings -> USB Configuration -> XHCI Hand-off -> Enabled
- Settings -> Software Guard Extensions(SGX) -> Disabled
- Settings -> Trusted Computing -> Security Device Support -> Disabled
- Boot -> CSM Support -> Disabled


## USB

- Format: Mac OS Extended.
- Schema: GUID Partition Map       

Follow Apple's instruction on how to use "createinstallmedia" command [https://support.apple.com/en-us/HT201372](https://support.apple.com/en-us/HT201372)

## Opencore EFI

Compile latest opencore from source, at the time of writing, it's at version 0.5.7

### ACPI 
- SSDT-EC-USBX.aml
- SSDT-HPET.aml
- SSDT-PLUG.aml
- SSDT-PMC.aml

### Driver
- VBoxHfs.efi
- ApfsDriverLoader.efi
- OpenRuntime.efi

### Kext
- Lilu.kext
- VirtualSMC.kext
- WhateverGreen.kext
- AppleALC.kext - Compile from source for latest version, it has fix for AppleHDA race condition
- IntelMausi.kext
- USBInjectAll.kext - Only needed for installation media
- USBPorts.kext - Refer post installation
- SMCProcessor.kext
- SMCSuperIO.kext

### config.plist

- Use `config_usb.plist` for installation media.
- Use `config.plist` for internal boot disk.


## Post Install

### Configure USB
Follow this guide: [https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/](https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/)
[USBMAP.md](USBMAP.md) 


### For sleep to work properly

```
sudo pmset hibernatemode 0
sudo pmset proximity 0
```
