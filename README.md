
# HP-15-dc1010nr-hackintosh

https://blog.hibobmaster.com/hp-15-dc1010nr-hackintosh 「Chinese」


**Support to macOS Monterey** | **Tested on Catalina v10.15.7 Big Sur 11.6 (20G165) and Monterey 12.1**

OpenCore version: 0.7.7  <br>
Please download it from release: https://github.com/hibobmaster/HP-15-dc1010nr-hackintosh/releases

OpenCore version: 0.6.3 (Catalina and Big Sur)  <br>
https://down.sky-and-poem.fun/source/static/HP-15-dc1010nr-hackintosh-main.zip

HP-15-dc1010nr-hackintosh/暗影精灵5-OpenCore-EFI

| HardWare |                                                    |
| -------- | -------------------------------------------------- |
| CPU      | i7-9750H                                           |
| iGPU     | Intel UHD Graphics 630                             |
| dGPU     | GTX1650                                            |
| Audio    | Realtek ALC295                                     |
| Disk     | HP SSD EX920 + Netac SSD                           |
| Wireless | Wireless-AC 9560/BCM94352z                                   |
| Ethernet | Realtek 8111/8168/8411 PCI Express Gigabit Etherne |

**Remember to change PM981 NVME even there is a NvmeFix.kext. (Potential problems)**

## Normal

* iGPU(GTX1650 is not supported)
* Sleep
* Battery
* Speakers、Microphone、Camera
* Cable network, Native wireless, Bluetooth
* Trackpad Gestures and Physical buttoms
* NVME and Sata Trim
* ...

## Abnormal

Due to HDMI port is conjuncted with dGPU, if you need external display, try to  use type-c

## Explanations

1. **iGPU: PciRoot(0x0)/Pci(0x2,0x0)**
* AAPL,ig-platform-id: 00009B3E
* enable-dpcd-max-link-rate-fix
* dpcd-max-link-rate 

Without above two args，you may stuck on or near `IOConsoleUsers:gIOScreenLock.../gIOLockState`

2. **Audio: PciRoot(0x0)/Pci(0x1F,0x3)**

Layout-id = 3

3. **Native wireless and bluetooth**

Intel Wi-Fi Drivers: https://github.com/OpenIntelWireless/itlwm

Intel Bluetooth Drivers: https://github.com/OpenIntelWireless/IntelBluetoothFirmware

> `itlwm.kext` uses Apple's IOEthernet rather than IO80211.
> Spoofing into Ethernet does not affect performance.

**Now use AirportItlwm.kext instead, so heliport is no longer needed.**

4. **Non-original battery prompt when startup**

This happens when you just used an USB bootloader or shutdown computer abnormally
**Press the battery button for more than 10s, then start computer again, the prompt will be missing**

5. **For iservice**: 

You need to use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to genrate your MLB、SystemSerialNumber、SystemUUID
Please read :
https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial

6. **Built-in Retina Display**

![Snipaste_2020-10-26_07-42-03.png](https://i.loli.net/2020/10/26/OnlQAGmu9JsNTxg.png)

It is convenient to use [one-key-hidpi](https://github.com/xzhih/one-key-hidpi) to enable macOS HIDPI and native display settings.

## Demonstration
![Screen Shot 2021-08-28 at 4 22 06 PM](https://user-images.githubusercontent.com/32976627/131211672-9231ec46-0755-4f9c-93c0-2ccd0542f201.png)
![Big Sur.png](https://i.loli.net/2020/11/26/gPmIFCxsE1tSjv2.png)
![](https://i.loli.net/2020/10/25/cl5RHLF3smzrMWh.png)

![Snipaste_2020-10-25_21-40-12.png](https://i.loli.net/2020/10/25/d6JQipSgfoH7Fal.png)

![Snipaste_2020-10-25_21-40-28.png](https://i.loli.net/2020/10/25/bHk3ULG4PAjx7Qq.png)

![Snipaste_2020-10-25_22-32-27.png](https://i.loli.net/2020/10/25/VKvZSdE3lani65O.png)
