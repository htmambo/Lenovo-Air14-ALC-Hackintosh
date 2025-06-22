# Lenovo-XiaoXin-Air14-ALC-hackintosh

![release version](https://img.shields.io/github/v/release/htmambo/morefine-S500-Hackintosh?style=for-the-badge) 

[![OpenCore version](https://img.shields.io/badge/OpenCore-1.0.5-informational.svg)](https://github.com/acidanthera/OpenCorePkg)![MacOS version](https://img.shields.io/badge/Tahoe-16.0%2025A5279m-informational.svg)![MacOS version](https://img.shields.io/badge/Sequoia-15.5%2024F74-informational.svg)![MacOS version](https://img.shields.io/badge/Sonoma-14.7.2%2023H309-informational.svg)![MacOS version](https://img.shields.io/badge/Catalina-10.15.7%2019H2026-informational.svg)

## 说明
1. 睡眠唤醒后亮度调节功能键`Fn+F5`和`Fn+F6`会失效，取而代之的是`Fn+P`和`Fn+K`，暂不清楚啥原因。

### 配置

---

部件|型号|是否支持
:-|:-|:-|
CPU|AMD Ryzen 5 5500U|支持
核显|AMD Radeon Vega 5|支持
网卡|Intel AX200|支持
硬盘|三星PM981A|不支持，更换PM9A1解决
触控屏|I2C HID|支持
键盘|PS2 controller|支持
蓝牙|Intel AX200|支持
HDMI输出||支持
音频/3.5耳机接口|ALC257|支持
内存|镁光DDR4 3200MHz|支持
USB|XCH0、XHC1|支持

---
## 了解你的EFI

---
### ACPI

SSDT | 作用
:---------|:---------
SSDT-ALS0 | NootedRed提供，用于屏幕亮度调整
SSDT-CPUR | 用于MacOS识别CPU，必须
SSDT-PNLF | NootedRed提供，用于屏幕亮度调整
SSDT-SBUS-MCHC | 解决AppleSMBus
SSDT-XOSI | MAC和WIN的ACPI功能，双系统必须

---
### Kexts

Kext | 作用
:---------|:---------
AMDRyzenCPUPowerManagement | AMD CPU 电源管理
AppleALC | 音频驱动
Lilu | 必备
RestrictEvents | CPU改名
SMCProcessorAMD | AMDRyzenCPUPowerManagement的附属
SMCBatteryManager | 电池管理
VirtualSMC | 必备
VoodooPS2Controller | PS/2 键盘，需要在config中禁用voodoops2 input以避免与i2c的input冲突，不影响使用
NootedRed | AMD核显驱动
VoodooI2C | 触控板或触屏驱动
VoodooI2CHID | 触控板或触屏驱动
AirportItlwm | 英特尔网卡驱动，注意不同的系统有不同的kext
BlueToolFixup | 蓝牙驱动，Monterey及以上版本中搭配IntelBluetoothFirmware使用
IntelBluetoothFirmware | 蓝牙驱动
IntelBluetoothInjector | 蓝牙驱动,在Big Sur中搭配IntelBluetoothFirmware使用
IntelBTPatcher | 蓝牙驱动,在Big Sur及以下版本中搭配IntelBluetoothFirmware使用

---

## 截屏

![开机画面](ScreenShots/boot.png)
![Tahoe](ScreenShots/about_for_tahoe.png)
![Sequoia](ScreenShots/about_for_sequoia.png)
![Sonoma](ScreenShots/About_for_Sonoma.png)
![Catalina](ScreenShots/about_for_catalina.png)
![Hackintool_Misc](ScreenShots/Hackintool_Misc.png)
![声音](ScreenShots/Audio.png)

### 以下为MyDevices.kext中的定制结果
![硬盘](ScreenShots/KIOXIA_NVME.png)
![USB定制](ScreenShots/USB.png)
![鼠标定制](ScreenShots/mouse.png)


### 致谢

---
感谢NootedRed的开发者们，使得AMD核显黑苹果成为可能
>https://github.com/NootInc/NootedRed

以及zabdottler的教程和指导
>https://github.com/zabdottler/Lenovo-Yoga-16S-hackintosh
