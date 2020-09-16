# OpenCore EFI

Download OpenCore 0.6.2 **RELEASE** from [here](https://github.com/acidanthera/OpenCorePkg/releases/download/0.6.2/OpenCore-0.6.2-RELEASE.zip)

## ACPI 
- SSDT-EC-USBX.aml
- SSDT-PLUG.aml
- SSDT-HPET.aml
- SSDT-PMC.aml

## Driver
- [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/raw/master/Drivers/HfsPlus.efi)
- OpenRuntime.efi - Included in OpenCore package

## Kext - Make sure to download RELEASE version
- [Lilu.kext](https://github.com/acidanthera/Lilu/releases/download/1.4.8/Lilu-1.4.8-RELEASE.zip)
- [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases/download/1.1.7/VirtualSMC-1.1.7-RELEASE.zip)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases/download/1.4.3/WhateverGreen-1.4.3-RELEASE.zip)
- [AppleALC.kext](https://github.com/acidanthera/AppleALC/releases/download/1.5.3/AppleALC-1.5.3-RELEASE.zip)
- [IntelMausi.kext](https://github.com/acidanthera/IntelMausi/releases/download/1.0.3/IntelMausi-1.0.3-RELEASE.zip)
- [USBInjectAll.kext](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/RehabMan-USBInjectAll-2018-1108.zip) - Only needed for installation media
- USBPorts.kext - [Refer post installation](POST_INSTALL.md)
- SMCProcessor.kext - Included in VirtualSMC package
- SMCSuperIO.kext - Included in VirtualSMC package

## Tools
- [modGRUBShell.efi](https://github.com/datasone/grub-mod-setup_var/releases/download/1.1/modGRUBShell.efi)
- OpenShell.efi - Included in OpenCore package
- ResetSystem.efi - Included in OpenCore package
- CleanNvram.efi - Included in OpenCore package

## config.plist

- Use `config_usb.plist` for installation media(USB). Rename it to `config.plist`.
- Use `config.plist` for internal boot disk.

## EFI Folder Structure

### USB
```
EFI
├── BOOT
│   └── BOOTx64.efi
└── OC
    ├── ACPI
    │   ├── SSDT-EC-USBX.aml
    │   ├── SSDT-HPET.aml
    │   ├── SSDT-PLUG.aml
    │   └── SSDT-PMC.aml
    ├── Bootstrap
    │   └── Bootstrap.efi
    ├── Drivers
    │   ├── HfsPlus.efi
    │   └── OpenRuntime.efi
    ├── Kexts
    │   ├── AppleALC.kext
    │   ├── IntelMausi.kext
    │   ├── Lilu.kext
    │   ├── SMCProcessor.kext
    │   ├── SMCSuperIO.kext
    │   ├── USBInjectAll.kext
    │   ├── VirtualSMC.kext
    │   └── WhateverGreen.kext
    ├── OpenCore.efi
    ├── Tools
    │   ├── CleanNvram.efi
    │   ├── OpenShell.efi
    │   ├── ResetSystem.efi
    │   └── modGRUBShell.efi
    └── config.plist
```

### SSD/NVME/HDD
```
EFI
├── BOOT
│   └── BOOTx64.efi
└── OC
    ├── ACPI
    │   ├── SSDT-EC-USBX.aml
    │   ├── SSDT-HPET.aml
    │   ├── SSDT-PLUG.aml
    │   └── SSDT-PMC.aml
    ├── Bootstrap
    │   └── Bootstrap.efi
    ├── Drivers
    │   ├── HfsPlus.efi
    │   └── OpenRuntime.efi
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
    ├── Tools
    │   ├── CleanNvram.efi
    │   ├── OpenShell.efi
    │   ├── ResetSystem.efi
    │   └── modGRUBShell.efi
    └── config.plist

```
