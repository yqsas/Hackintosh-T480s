## 简介

- Lenovo ThinkPad T480s Hackintosh EFI ，包含基础驱动，修改三码后开箱即用。
- 适用版本：macOS Catalina 10.15.3。
  > 如需 10.14.x 版本，请切换至 mojave-10.14.6 分支

- This repository is a working progress of the clover folder used to install catalina on Lenovo ThinkPad T480s.

## 前提

1. 更换自带 pm981 的硬盘，截止 10.13.6 版本无解，Mojave 未测试
2. 更换自带 intel 无线网卡，本人使用 BCM94352Z Dell DW1560

## 硬件说明

### 硬件配置

Lenovo ThinkPad T480s

- Intel i7-8550U
- 16GB RAM
- Samsung SM961 NVMe SSD
- Dell DW1560 Wireless (Intel AC8265 不可用）
- 1440p 分辨率

### 硬件使用状态

* [x] 集成显卡 UHD620
* [x] 屏幕亮度调节（小太阳）
* [x] 有线网
* [x] 无线网（Dell DW1560）
* [x] 蓝牙（Dell DW1560）
* [x] 电池状态
* [x] hidpi (1440*810 完美）
* [x] 声音
* [x] SD 卡读取
* [x] 触控板（手势完美）
* [x] 小红点
* [ ] ~~独立显卡 mx150~~
* [ ] ~~指纹识别器~~

## 使用方法

修改`EFI/CLOVER/config.example.plist` 为 `config.plist`。

1. 编辑 `config.plist` 中的 SMBIOS 内容：
    - BoardSerialNumber: 修改示例编码中的 Z 字母为随机数字与字母
    - SerialNumber: 修改示例编码中的 Z 字母为随机数字与字母
    - SmUUID: 随机生成一个 UUID，通过 [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/) 获取

2. 编辑 `config.plist` 中的 RtVariables 内容：

    - MLB：使用上面第一步中修改后的 BoardSerialNumber

3. 编辑 `config.plist` 中的 SystemParameters 内容：
    - CustomUUID：使用第一步中生成的 UUID

4. （可选）蓝牙如果不可用，请将 kexts/Other/目录中的`BrcmBluetoothInjector.kext`、`BrcmFirmwareData.kext`、`BrcmPatchRAM2.kext` 拷贝到 `/Library/Extensions` 目录下，并重建系统缓存：`sudo kextcache -i /`

## 推荐工具

- [one-key-hidpi](https://github.com/xzhih/one-key-hidpi/blob/master/README-zh.md) : 一键开启 macOS HiDPI

## 遗留问题

1. Hidpi 只能使用 1440*810，超过此分辨率的情况下休眠后唤醒会花屏（雪花点）
2. 蓝牙功能不稳定，无法通过隔空投送发送文件，网卡硬件限制

## 致谢

- [linusyang92/macOS-ThinkPad-T480s](https://github.com/linusyang92/macOS-ThinkPad-T480s)
- [kk1987/T480s-hackintosh](https://github.com/kk1987/T480s-hackintosh)
- [触控板驱动：VoodooSMBus.kext](https://github.com/leo-labs/VoodooSMBus)
- ThinkPad X1 Carbon 黑果群 (QQ 群 Njc4Mzc3NzQ3)
