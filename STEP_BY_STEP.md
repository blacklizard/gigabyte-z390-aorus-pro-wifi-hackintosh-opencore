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

At the time of writing, it's at version 0.5.8, Download 0.5.8 from [here](https://github.com/acidanthera/OpenCorePkg/releases/download/0.5.8/OpenCore-0.5.8-RELEASE.zip)

### ACPI 
- SSDT-EC-USBX.aml
- SSDT-PLUG.aml
- SSDT-HPET.aml
- SSDT-PMC.aml

### Driver
- [VBoxHfs.efi](https://github.com/acidanthera/AppleSupportPkg/releases/download/2.1.7/AppleSupport-2.1.7-RELEASE.zip)
- OpenRuntime.efi - Included in OpenCore package

### Kext
- [Lilu.kext](https://github.com/acidanthera/Lilu/releases/download/1.4.4/Lilu-1.4.4-RELEASE.zip)
- [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases/download/1.1.3/VirtualSMC-1.1.3-RELEASE.zip)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases/download/1.3.9/WhateverGreen-1.3.9-RELEASE.zip)
- [AppleALC.kext](https://github.com/acidanthera/AppleALC/releases/download/1.4.9/AppleALC-1.4.9-RELEASE.zip)
- [IntelMausi.kext](https://github.com/acidanthera/IntelMausi/releases/download/1.0.2/IntelMausi-1.0.2-RELEASE.zip)
- [USBInjectAll.kext](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/RehabMan-USBInjectAll-2018-1108.zip) - Only needed for installation media
- USBPorts.kext - Refer post installation
- SMCProcessor.kext - Included in VirtualSMC package
- SMCSuperIO.kext - Included in VirtualSMC package

### Tools
- [modGRUBShell.efi](https://github.com/datasone/grub-mod-setup_var/releases/download/1.1/modGRUBShell.efi)
- OpenShell.efi - Included in OpenCore package
- ResetSystem.efi - Included in OpenCore package

### config.plist

- Use `config_usb.plist` for installation media.
- Use `config.plist` for internal boot disk.

### Folder Structure of EFI

```
EFI
├── BOOT
│   └── BOOTx64.efi
└── OC
    ├── ACPI
    │   ├── SSDT-EC-USBX.aml
    │   ├── SSDT-PLUG.aml
    │   ├── SSDT-HPET.aml
    │   └── SSDT-PMC.aml
    ├── Bootstrap
    │   └── Bootstrap.efi
    ├── Drivers
    │   ├── OpenRuntime.efi
    │   └── VBoxHfs.efi
    ├── Kexts
    │   ├── AppleALC.kext
    │   ├── IntelMausi.kext
    │   ├── Lilu.kext
    │   ├── SMCProcessor.kext
    │   ├── SMCSuperIO.kext
    │   ├── USBPorts.kext
    │   ├── VirtualSMC.kext
    │   └── WhateverGreen.kext
    ├── OpenCore.efi
    ├── Resources
    │   ├── Audio
    │   ├── Font
    │   ├── Image
    │   └── Label
    ├── Tools
    │   ├── CleanNvram.efi
    │   ├── OpenShell.efi
    │   ├── ResetSystem.efi
    │   └── modGRUBShell.efi
    └── config.plist
```


## Post Install

### Configure USB
Follow this guide: [https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/](https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/)
[USBMAP.md](USBMAP.md) 


### For sleep to work properly

```
sudo pmset hibernatemode 0
sudo pmset proximitywake 0
```
