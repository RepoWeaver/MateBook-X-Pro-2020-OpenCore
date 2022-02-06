# MateBook X Pro 2020 | Opencore

<p align="center">
<img src="https://user-images.githubusercontent.com/91159194/148530343-f93d5431-80c5-458b-afe8-e00ff4926b7b.png" width="70%" alt="Huawei Big Sur 11.0" />
</p>
<p align="center">
<a href="https://consumer.huawei.com/en/laptops/matebook-x-pro-2020/" target="_blank"><img src="https://img.shields.io/badge/Model-MACHC_WAX9-green.svg" /></a>
<a href="https://consumer.huawei.com/en/support/laptops/matebook-x-pro-2020/" target="_blank"><img src="https://img.shields.io/badge/BIOS-1.12-orange.svg" /></a>
<a href="https://github.com/RepoWeaver/MateBook-X-Pro-2020-OpenCore/releases" target="_blank"><img src="https://img.shields.io/badge/Download-Releases-blue.svg" /></a>
</p>

You Must **Change SMBIOS** to use **iCloud Services**

Currently working on my Personal Machine, so only **stable versions** will be released

#### Compatible macOS Versions:
<div align="Left">
	
| **macOS** | **Version** | **Status** | **OpenCore Version** |
| --- | --- | --- | --- |
| <div align="Center"> Monterey | <div align="Center"> 12.1 (21GC52) | <div align="Center"> Stable | <div align="Center"> OpenCore 0.7.6 |
| <div align="Center"> Big Sur | <div align="Center"> 11.6.2 (20G314) | <div align="Center"> Stable | <div align="Center"> OpenCore 0.7.6 |


</div>

<strong>macOS Monterey Support Completed, Will keep maintaining</strong></summary>

- Follow Dortania's steps for [making the installer in macOS](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#setting-up-the-installer)

If you find my work useful:
* please consider **giving** it **a star** to make it more visible.
* please consider **donating** to keep on maintaining this repo. <a href="https://www.buymeacoffee.com/repoweaver" target="_blank"><img src="https://img.shields.io/badge/Buy me a coffee-orange.svg" /></a>


### DISCLAIMER

- For best results, read the entire README before you start and follow the install instruction throughly.
- I am not responsible for any damages you may cause.
- **This is not a support forum**.
- Should you find an error or improve anything — whether in the config or in the documentation — please consider opening an issue or pull request.
- **Complete EFI packs** are available in the [**Releases**](https://github.com/RepoWeaver/MateBook-X-Pro-2020-Opencore/releases) page (please, refer to the rightside menu).
- **EFI** is configured with **Monterey** or **Big Sur** in mind
- **EFI** is configured for loading macOS **from internal NVMe SSD** 

**When booting, as of the current moment. You will need to open and close lid if you have a black screen.**

	
	
**This repository is for personal purposes only.**


## Introduction

This repo contains the files needed for getting macOS working on a **Huawei MateBook X Pro (2020 Edition)** laptop with OpenCore.
* This is intended to create a "fully" functional (as far as possible) hackintosh for the Huawei Matebook X Pro.
* The project can be considered **stable**.
* With each new release of macOS we need to resolve each new "minor issue" we run into. 
* If you would like to get started with creating a hackintosh on your MBXP but have non experience, I would highly recommend following [**Dortania's OpenCore Install guide**](https://dortania.github.io/OpenCore-Install-Guide/) and then returning here for troubleshooting or last improvements.


### Summary

- The **compatibility** is **very good** for the most part, most of the stuff works like it would on a real MacBook, including camera, audio, touchpad, iCloud services.
- The **experience** is **pleasant**, as the laptop is smooth and responsive under macOS Big Sur/Catalina.
- **Battery life** is **quite great** (from personal experience it **lasts from 4-6 hours** for light works depending on its age with a behaviour very similar to Windows 11.

(With the use of turbo boost disabled)
http://tbswitcher.rugarciap.com/

- The **Intel WiFi** card is soldered onto the motherboard, which means it can't be replaced with a Broadcom one, but the Intel card is now **functional albeit not operating at full speeds** (however it is fine for most use cases).
    * With the latest `AirportItlwm.kext` even **Handoff** and **Continuity** features are working, but with a very limited support for AirDrop and Apple Watch unlocking (see [Changelog for OpenIntelWireless release](https://github.com/OpenIntelWireless/itlwm/releases)).
    * For any issues about `AirportItlwm.kext` please refer first to [**OpenIntelWireless Troubleshooting page**](https://openintelwireless.github.io/itlwm/Troubleshooting.html#kernel-extension-loading-status) and then to [**OpenIntelWireless Gitter Page**](https://gitter.im/OpenIntelWireless/itlwm?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


### Generate your own SMBIOS Information

For privacy reasons, all SMBIOS information has been wiped out in the configuration file `EFI/OC/config.plist`. You need to generate your unique `SMBIOS` info by yourself (recommend to use [**CorpNewt's GenSMBIOS**](https://github.com/corpnewt/GenSMBIOS)), and inject them into your `config.plist`.
- With every **EFI update** you retrieve from [here](https://github.com/RepoWeaver/MateBook-X-Pro-2020-Opencore/releases), please, remember to transfer **your Device details** under `PlatformInfo -> Generic` in your `config.plist`.

<p align="center">

<img src="https://user-images.githubusercontent.com/91159194/148256043-38860f4b-71ba-4f32-9178-013eb2b1a7a1.jpg" width="70%" alt="About this Mac Monterey Working on" />
</p>
<p align="center">
Currently working on macOS Monterey Support 
</p>
<p align="center">
- Big Sur is running well (Config in Releases)
</p>

## Configuration

<div align="left">

| Specifications      | Details                                          |
| :--- | :--- |
| Computer model      | Huawei Matebook X Pro 2020                       |
| Processor           | Intel Core i5-10210U Processor @ 1.60 GHz        |
| Memory              | 16 GB LPDDR3 2133 MHz                            |
| Hard Disk           | WDC PC SN730 SDBPNTY-512G-1027                   |
| Integrated Graphics | NVIDIA GeForce MX250 / Intel(R) UHD Graphics 620 |
| Screen              | 3K Display @ 3000 x 2000 (13.9 inch)             |
| Sound Card          | Realtek ALC256                                   |
| Wireless Card       | Intel Dual Band Wireless-AC                      |
| Bluetooth Card      | Intel Bluetooth                                  |

</div>

**Intel Graphics** It will say Intel(R) UHD Graphics 630 or Intel HD Graphics CFL CRB 1536 MB with **Big Sur Releases**
	
	This is fine and will still work!!!


## Changelog

#### 2022 - January - 7th
See [**Current status**](https://github.com/RepoWeaver/MateBook-X-Pro-2020-OpenCore/releases)

## Status

- [x] **Intel(R) UHD 620** Graphics card  
- [x] **Intel(R) Wireless-AC** & **Intel(R) Bluetooth**
	
	(With Bluetooth, Downloading bit files affects bluetooth, bluetooth may just stop or crackle and this has always happened on Windos 10 and 11, it's just a really poor design from intel or Huawei)
- [x] **Power Management** with support for HWP (Intel Speed Shift & Intel SpeedStep) - Battery Life improvements - Depending on your CPUFriendFriend.kext file
- [x] **Sleep** and **Wake** (support for native macOS `hibernatemode3`)
- [x] **Hibernation** (support for native macOS `hibernatemode25` with `HibernationFixup.kext`)
- [x] **Battery support** with better memory access and integration of [Battery Information Supplement & Turbo Boost Disabled (Applicaition)]
- [x] **Automatic Backlight control** (Untested)
- [x] **Fixed Black Screen on boot** (Won't have to close and open lid anymore 🎉)
- [x] **Proper Power Management after wake from sleep**
- [x] I've noticed that when plugging in a display through a hub you may need to plug in twice (This has always happened, just pointing out something)
- [x] Backlight shortcuts (F1 [brightness level down] - F2 [brightness level up])
- [x] Volume shortcuts (F4 [mute] - F5 [audio level down] - F6 [audio level up])
- [x] **Audio** for **Realtek ALC256** card (via `AppleALC.kext` and `layout-id 97`)
- [x] **Speakers** (4 Channels) & Internal Mic
- [x] **Headphone** jack [2 in 1]  (via `ALCPlugFix`)
- [x] **HDMI 2.0** up to two 4K @60 Hz monitors (via LSPCON)
- [x] **Native Color Profile** for Display 3K
- [x] **TouchPad** and **native macOS gestures**
- [x] Touchscreen (Disabled) 
- [x] PCI Devices latency support and complete description for System Information app
- [x] **USB Ports Mapping** (Type-A:1 & Type-C:2) with proper power levels
- [x] **Thunderbolt Port** (limited support)
- [x] HD Camera
- [x] NVRAM native support

#### BIOS Settings

- [x] Disable Secure Boot, Disable TPM, Thunderbolt (If you want to)

<summary><strong>Notes</strong></summary>

1. **Intel Bluetooth** could not support some Bluetooth devices
2. **Touchscreen support is disabled by default** (Battery improvement)

#### Fixing Internal Speakers (taken from gnodipac886):

By default macOS only uses 2 out of your 4 speakers which sound muffled and are missing a lot of the high frequencies.

Enable surround sound to get a way better audio experience.

- Open Audio MIDI Setup from applications
- Click on the "+" symbol on the bottom left corner
- Click "Create Muti-Output Device"
- Check both of the Built-in Output options
- Select the newly created device in the menu bar
- Enjoy your music!

## Disabling CFG Lock and enabling DVMT 64 (BIOS patches):

There is the possibility of disabling CFG Lock and enabling dvmt 64. Disabling CFG Lock allows a better power management improvement. Enabling DVMT 64 allows 4K resolution in external screen. Both procedures (Customizing BIOS) are quite easy to follow, but you have to do very carefully and could brick your MBXP if you don't follow them step by step. Use them at your own risk!

(look at [this link](https://github.com/ske1996/Matebook-x-pro-2019-Hackintosh-newest/blob/main/readme-en.md#after-installation): "How to disable CFG Lock" and "Change dvmt to 64 mb" in "After installation" section).

These guides work without issue on the MateBook X Pro 2020 (tested with BIOS 1.19 and 1.21 versions). 

Each guide shows the changes to do in config.plist as well.
	

## Credits
Many great people.
- [Acidanthera](https://github.com/acidanthera)
- [Dortania's OC guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [OpenWireless project](https://github.com/OpenIntelWireless/itlwm)
- [profzei's Maintainer for Page Design](https://github.com/profzei/Matebook-X-Pro-2018)
- [dsdt-database](https://dsdt-database.monster/matebook-x-pro-2020-core-i5-10210u-opencore/)
- [gnodipac886](https://github.com/gnodipac886/MatebookXPro-hackintosh#activate-surround-sound-via-midi)
- [espitgn](https://github.com/espitgn) - Helping with Maintaining Monterey / Big Sur Support
- [RECOLE](https://GMML-LD7C-WUMJ-2ZEP-CAJV-Z66U-6AAR.com)
