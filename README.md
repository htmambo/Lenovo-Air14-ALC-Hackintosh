# Lenovo-XiaoXin-Air14-ALC-hackintosh

## 说明
1. 使用的是自编译的[NootedRed.kext](https://github.com/htmambo/NootedRed/releases)，添加了BFixup以及Seey6的代码(硬解代码只在`Montery`下生效)；
2. CPU默认关闭了CPB，如果需要开启请手动在AMD Power Gadget中打开(CPB状态睡眠唤醒后会自动保持睡眠前的状态)。

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
SSDT-PLUG-ALT | 用于MacOS识别CPU，必须
SSDT-SBUS-MCHC | 解决AppleSMBus
SSDT-XOSI | MAC和WIN的ACPI功能，双系统必须
SSDT-ALS0 | NootedRed提供，用于屏幕亮度调整
SSDT-PNLF | NootedRed提供，用于屏幕亮度调整

---
### Kexts
Kext | 作用
:---------|:---------
AMDRyzenCPUPowerManagement | AMD CPU 电源管理
AppleALC | 音频驱动
AppleMCEReporterDisabler | 关闭AppleIntelMCEReporter，避免在AMD CPU的设备上报错
Lilu | 必备
NVMeFix | NVMe硬盘电源管理
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
### 温度
可以通过关闭CPS(core performence boost）将温度控制在比较合适的范围，但是会损失一部分性能。可以通过UMAF在bios中关闭CPS，但是会影响其他系统比如windows的性能，建议是每次开机进系统后通过AMD Power Gadget关闭，至少目前是只能这样。

---
### 致谢

---
感谢NootedRed的开发者们，使得AMD核显黑苹果成为可能
>https://github.com/NootInc/NootedRed

以及zabdottler的教程和指导
>https://github.com/zabdottler/Lenovo-Yoga-16S-hackintosh
