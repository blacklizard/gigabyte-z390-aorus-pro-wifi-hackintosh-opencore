# Post Install

## Configure USB ports
Follow this guide: [https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/](https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/)

- [USBMAP.md](USBMAP.md) 

#### TL;DR 
> The physical port is the same, but how it is enumerated is different depending on what type of device is plugged-in - USB2.0 is an HS\*\* port and USB3.0/3.1 is an SS\*\* port. So as you can see, a single, physical USB3 port counts as 2x ports towards our 15-limit because either type of device can be plugged in to it.
>
> UtterDisbelief

## For sleep to work properly

```
sudo pmset hibernatemode 0
sudo pmset proximitywake 0
```

## iServices
To make sure you will be able to get iServices to work, skip signing in during installtion process.\
Generate an invalid serial using `GenSMBIOS` for `iMac19,1`, be really sure that the generated serial is invalid by cross checking it in apple webiste.

Once its validated to be invalid, use the generated serial, board serial and SmUUID in your `config.plist` under `PlatformInfo` section.\

Restart and sign in to your apple account, you should be able to use all the iServices
