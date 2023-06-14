# Lenovo-XiaoXin-Air14-ALC-hackintosh

## 说明

**本文内容摘抄自 [zabdottler](https://github.com/zabdottler/Lenovo-Yoga-16S-hackintosh)**

**本EFI仅供Big Sur到Sonoma系统正常使用**

**Catalina勉强可以使用，但是极易黑屏崩溃**

**在安装MacOS前请在config.plist中禁用nootedred.kext**

**机型信息已删除，请自行生成更换**

**OpneCore版本0.9.4 release**


---
### 存在的问题
1.睡眠

2.内置麦克风

3.偶尔会卡住

4.VCN（视频/图片硬件编解码）暂时还有问题，能使用但不确保问题，默认关闭，开启请添加-nredvcn至boot-args，具体请移至NootedRed页面查看最新进展

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
ECEnabler | 电池读取
Lilu | 必备
NVMeFix | NVMe硬盘电源管理
RestrictEvents | CPU改名
SMCAMDProcessor | AMDRyzenCPUPowerManagement的附属
SMCBatteryManager | 电池管理
VirtualSMC | 必备
VoodooPS2Controller | PS/2 键盘，需要在config中禁用voodoops2 input以避免与i2c的input冲突，不影响使用
NootedRed | AMD核显驱动
NullEthernet | 使无网口设备在MacOS可以登录iCloud
VoodooI2C | 触控板或触屏驱动
VoodooI2CHID | 触控板或触屏驱动
BrightnessKeys | 亮度调节按键
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
