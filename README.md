# Huananzhi X99E K4 Opencore (MacOS Monterey 12.x.x)

[OpenCore Legacy Patcher]: https://github.com/dortania/OpenCore-Legacy-Patcher/releases

![Screenshot](https://i.imgur.com/6eFolAP.png)


Hardware | Model
--- |:--:
![motherboard](https://i.imgur.com/rcyOyso.png) | Huananzhi X99E-K4 (Clarkdale Southbridge)
![bios](https://i.imgur.com/RmYixFt.png) | Aptio's V v3.01 (by American Megatrends (AMI)/Modified by Huananzhi)
![processor](https://i.imgur.com/K9VlfRK.png) | Intel Xeon (5th Gen) E5-2640v4 10 Cores/20 Threads@2,4Ghz
![dgpu](https://i.imgur.com/7TZmF2e.png) | AMD/Sapphire Radeon RX 580 Nitro+ 8GB VRAM@1411Mhz (Officially supported until MacOS Ventura)
![audio](https://i.imgur.com/A7RRuUn.png) | ALC897 (in-build)
Ethernet | Realtek RTL8168H
![ddr4](https://i.imgur.com/2oda3vY.png) | Corsair ValueSelect 32GB(4x8GB) DDR4@2133Mhz
![ssd](https://i.imgur.com/pozDx4X.png) | Kingston A400 240GB (TLC PS3111 Controller, testing drive)
![nvme](https://i.imgur.com/xbsV0Ia.png) | Kioxia Exceria Pro 1TB SSD Nvme (TLC PS5018 Controller)
---


### Works:
---
<details>

- Installer Boot ✅ (Installation on SSD: ~30/35 minutes)

- System Boot ✅

- USB Ports ✅

- Screen ✅ (1336x768, 1080x1920)

- Audio Card ✅ (Inputs and Outputs)

- Ethernet ✅

- PCI Express Ports ✅

- Sleep Mode ✅

 
</details>


### IMPORTANT NOTES:
---

## For use AMD Graphics only:

1. Add the boot-arg:

- "**radpg=15**" for enabling 3D Acceleration (In almost all 2017 or older GPUs, Eg: RX 580, RX 470, R9 Fury X, HD 7730, etc).

- "**agdpmod=pikera**" for try enabling drivers (In almost all 2018 or newer GPUs, Eg: Vega 56, Radeon VII, RX 5700XT, RX 6600, etc).
From *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* with your graphic card data (Eg: AMD Radeon RX 5700XT and Bermuda HDMI Audio [Navi Series])

---

## For use Nvidia Graphics only:

1. Add the boot-arg "**nv_disable=1**" (for using Vesa drivers); later, create a new table like this (for enabling Nvidia Drivers):

![nvidiatable](https://i.imgur.com/1crQGj1.png)

**Usually for Pascal (GTX1000 Series), Maxwell (GTX900 Series) and Kepler (GTX600/700 Series) GPUs.***

all on *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*; if Nvidia GPU isn't recognize after that, add "**agdpmod=pikera**" boot-arg too.

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* (Eg: Nvidia GeForce GTX 1070Ti and Nvidia HDMI Output)

3. Download and install [OpenCore Legacy Patcher] for try patch your GPU (Pascal *GTX1000* and older generations *GTX900, 700, 600* are supported; **ALL RTX MODELS AREN'T SUPPORTED**), later, go to *config.plist --> NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82* and remove "**nv_disable=1**" and reboot.

---

## What audio codec I can use?:

With boot-arg "**alcid=**":

- If you have the Realtek ALC897, you can use these layouts: *11, 12, 13, 21, 23, 66, 69, 77, 98, 99*

--- 

## Do you want Wi-Fi on your PC?:

- If is a TP-Link, Edimax, Ralink or Mediatek wireless adapter, use the D-Link Utility (https://github.com/chris1111/D-LinkUtility-Package) or Wireless USB Adapters: (https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter) (*see the supported devices*)

- If is some Asus, TP-Link or Intel PCI wireless adapter, use the AirportItlwm (https://github.com/OpenIntelWireless/itlwm) (*see the supported devices on https://openintelwireless.github.io/itlwm/Compat.html*); for Asus and TP-Link adapters, check if the used Wi-Fi card is made by Intel.

---

## Do you only have your Android Phone/Device on hand?:

 1. Download HoRNDIS (https://github.com/jwise/HoRNDIS) and put it on your Hackintosh installation.

 2. Connect your device via USB and enable USB Tethering.




