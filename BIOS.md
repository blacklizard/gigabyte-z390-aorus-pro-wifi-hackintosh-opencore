# BIOS Configuration

BIOS version: `F12j`

- Load Optimized Defaults
- Settings -> IO Ports -> Internal Graphics -> Enabled
- Settings -> IO Ports -> DVMT Pre-Allocated -> 64M
- Settings -> IO Ports -> Wi-Fi -> Disabled
- Settings -> IO Ports -> Above 4G Decoding -> Enabled
- Settings -> IO Ports -> Wake on LAN Enable -> Disabled
- Settings -> IO Ports -> USB Configuration -> Legacy USB Support -> Disabled
- Settings -> IO Ports -> USB Configuration -> XHCI Hand-off -> Enabled
- Settings -> Miscellaneous -> Software Guard Extensions(SGX) -> Disabled
- Settings -> Miscellaneous -> Trusted Computing -> Security Device Support -> Disabled
- Boot -> CSM Support -> Disabled
- Boot -> CFG Lock -> Disabled

## Hidden BIOS setting
This setting can be modified using [modGRUBShell.efi](https://github.com/datasone/grub-mod-setup_var/releases/download/1.1/modGRUBShell.efi)
⚠️: These offset are only valid for the specific firmware version! Do not try to execute these commands on a different firmware! 
The modified variables will reset itself when you restore / revert to optimised defaults. 
Everytime BIOS is reset, you will need to reconfigure the hidden setting or else you will not be able to boot, you have been warned

#### Required setting - Only for F11 and lower
- Disable CFG Lock 

| Firmware Version | Command              |
|------------------|----------------------|
| F9, F10, F11     |`setup_var 0x5C1 0x00`|

#### Optional Setting
- Turn off motherboard LED

| Firmware Version | Command               |
|------------------|-----------------------|
| F11              |`setup_var 0x16FE 0x00`|
|                  |`setup_var 0x16FF 0x00`|
|                  |`setup_var 0x1700 0x00`|
|                  |`setup_var 0x1701 0x00`|
