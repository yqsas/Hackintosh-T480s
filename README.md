# 简介
- Lenovo ThinkPad T480s Hackintosh EFI ，包含基础驱动，修改三码后开箱即用。
- 适用版本：macOS Mojave 10.14.0 ~ 10.14.4。

# 前提
1. 更换自带pm981的硬盘，截止10.13.6版本无解，Mojave未测试
2. 更换自带intel无线网卡，本人使用 BCM94352Z Dell DW1560
3. efi里使用的键盘触控板驱动可支持多指手势，但是使用之前必须在bios里面禁用小红点功能
    > 小红点与触控板无法并存，重启后可在设置里勾选再取消勾选『轻点来点按』，解决误触问题

4. 如果需要小红点，请使用backup/VoodooPS2Controller.kext替换kext/other中的ApplePS2SmartTouchPad.kext，并使用backup/SSDT-KBD.aml替换ACPI/patched中的同名文件
    > 此方式触控板仅支持单指手势，使用键盘容易误触，建议在bios里禁用触控板

# 硬件说明
### 硬件配置
Lenovo ThinkPad T480s
- Intel i7-8550U
- 16GB RAM
- Samsung SM961 NVMe SSD
- Dell DW1560 Wireless (Intel AC8265 不可用)
- 1440p 分辨率

## 硬件使用状态
* [x] 集成显卡uhd620，显存2048M
* [x] 屏幕亮度调节(小太阳)
* [x] 有线网
* [x] 无线网（Dell DW1560）
* [x] 蓝牙（Dell DW1560）
* [x] 电池状态
* [x] hidpi (1440*810 完美)
* [x] 声音
* [x] SD卡读取
* [x] 触控板 (可选)
* [ ] 小红点 (可选)
* [ ] ~~独立显卡mx150~~
* [ ] ~~指纹识别器~~

# 使用方法
修改`EFI/CLOVER/config.example.plist` 为 `config.plist`。

1. 编辑 `config.plist` 中的SMBIOS内容:
    - BoardSerialNumber: 修改示例编码中的Z字母为随机数字与字母
    - SerialNumber: 修改示例编码中的Z字母为随机数字与字母
    - SmUUID: 随机生成一个UUID，通过 [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/) 获取

2. 编辑 `config.plist` 中的RtVariables内容:
    -  MLB：使用上面第一步中修改后的BoardSerialNumber

3. 编辑 `config.plist` 中的SystemParameters内容:
    - CustomUUID：使用第一步中生成的UUID

# 推荐工具
- [one-key-hidpi](https://github.com/xzhih/one-key-hidpi/blob/master/README-zh.md) : 一键开启 macOS HiDPI

# 遗留问题
1. Hidpi只能使用1440*810，超过此分辨率的情况下休眠后唤醒会花屏（雪花点）

# 致谢
- [linusyang92/macOS-ThinkPad-T480s](https://github.com/linusyang92/macOS-ThinkPad-T480s)
- [kk1987/T480s-hackintosh](https://github.com/kk1987/T480s-hackintosh)
- ThinkPad X1 Carbon黑果群(QQ群 Njc4Mzc3NzQ3)
- [ApplePS2SmartTouchPad.kext](https://osxlatitude.com/forums/topic/1948-elan-focaltech-and-synaptics-smart-touchpad-driver-mac-os-x/)
