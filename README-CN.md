# 小米笔记本PRO安装MacOS High Sierra & Sierra 使用说明

让你的小米PRO笔记本吃上黑苹果



## 支持列表

* 支持10.13 / 10.12.6
* CPU为第八代，原生支持
* 显卡仿冒支持，platform-id为0x19160000，注入信息通过 `/CLOVER/ACPI/patched/SSDT-Config.aml` 加载
* 声卡为ALC298，采用AppleALC仿冒，layout-id为99，注入信息位于 `/CLOVER/ACPI/patched/SSDT-Config.aml`
* 触摸板驱动程序使用VoodooI2C，支持多手势，触摸板开机可正常使用，不漂移，无需唤醒
* 其他ACPI补丁修复使用hotpatch方式，文件位于 `/CLOVER/ACPI/patched` 中
* USB遮盖使用 `/CLOVER/kexts/Other/USBInjectAll_patched.kext`



## 更新日期：

* 10-14-2017
    * EFI更新，触摸板工作正常

* 10-17-2017
    * EFI更新，修正显卡驱动
    * 增加HDMI Audio声音输出
    * 驱动更新：
        * Lilu v1.2.0 
        * AppleALC v1.2.1
        * IntelGraphicsDVMTFixup v1.2.0
        * AirportBrcmFixup v1.1.0
    * 驱动修复：
        * IntelGraphicsFixup v1.2.0 

* 10-18-2017
    * 经测试显卡驱动不如第一版的好，现将显卡驱动恢复为仿冒0x19160000
    * ACPI修复
    * 驱动程序修正
    * 去掉USBInjectAll采用SSDT-UIAL.aml内建USB设备

* 10-19-2017
    * 显卡驱动正常
    * 触摸板开机正常，睡眠唤醒后多手势使用正常
    * 睡眠正常
    * 电池信息正常

* 10-31-2017
    * 更新声卡驱动，修复耳机问题
    * 新驱动增加layoutid：13
    * 支持四节点，支持耳麦自由切换，Mic/LineIn工作正常
      ![ALC298for小米Pro声卡驱动安装](http://ous2s14vo.bkt.clouddn.com/ALC298for小米Pro声卡驱动安装.png)

* 11-2-2017
    * Lilu v1.2.0更新，支持10.13.2Beta
    * AppleALC更新，使用最新修正版Lilu联合编译，解决10.13.1更新后无法驱动的问题

* 11-5-2017
    * 整合 `AppleALC_ALC298_id13_id28.kext` 驱动到EFI
    * EFI目录下添加ALCPlugFix目录，请安装完成后进入ALCPlugFix目录，双击 `install双击自动安装.command` 安装耳机插入状态修正守护程序
    * 修正Drivers64UEFI，解决无法安装问题
    * 更新apfs.efi到10.13.1版本

* 11-7-2017
    * Lilu v1.2.1目前还不稳定，存在无法进入系统的风险，所以降级到v1.2.0版本
    * AppleALC降级到V1.2.0

    **EFI暂不支持macOS 10.13.2Beta版本的安装，Lilu不抽风后会持续更新**

* 1-25-2018

    * 支持10.13.x安装使用
    * 更新`VoodooI2C`到2.0.1版本，支持多手势，触摸板开机可正常使用，不漂移，无需唤醒
    * 修复电量百分比不刷新的问题
    * 修复声卡睡眠唤醒无声音的问题
    * 修复屏幕亮度无法保存的问题
    * 更新`Lilu` v1.2.2
    * 更新`AppleALC` v1.2.2 支持小米Pro，注入ID:99

* 4-13-2018

    * 发布Clover v2.4 r4438小米笔记本PRO专用安装程序

        ![Clover_v2.4k_r4438](http://7.daliansky.net/clover4438/2.png)




## 鸣谢

[RehabMan](https://github.com/RehabMan) Updated [OS-X-Clover-Laptop-Config](https://github.com/RehabMan/OS-X-Clover-Laptop-Config) and [Laptop-DSDT-Patch](https://github.com/RehabMan/Laptop-DSDT-Patch) and [patch-nvme](https://github.com/RehabMan/patch-nvme) and [OS-X-USB-Inject-All](https://github.com/RehabMan/OS-X-USB-Inject-All) for maintenance

[vit9696](https://github.com/vit9696) Updated [Lilu](https://github.com/vit9696/Lilu) and [AppleALC](https://github.com/vit9696/AppleALC) and [WhateverGreen](https://github.com/vit9696/WhateverGreen)  for maintenance

[Pike R. Alpha](https://github.com/Piker-Alpha) Updated [ssdtPRGen.sh](https://github.com/Piker-Alpha/ssdtPRGen.sh) and [AppleIntelInfo](https://github.com/Piker-Alpha/AppleIntelInfo) and [HandyScripts](https://github.com/Piker-Alpha/HandyScripts) for maintenance

[toleda](https://github.com/toleda), [Mirone](https://github.com/Mirone) and certain others for audio patches and layouts



## 安装

请参考详细的安装教程（中文版）[macOS安装教程兼小米Pro安装过程记录](https://blog.daliansky.net/MacOS-installation-tutorial-XiaoMi-Pro-installation-process-records.html).
完整的EFI压缩版请访问 [releases](https://github.com/daliansky/XiaoMi-Pro/releases) 页面.



## 关于打赏

如果您认可我的工作，请通过打赏支持我后续的更新

| 微信                                       | 支付宝                                      |
| ---------------------------------------- | ---------------------------------------- |
| ![wechatpay_160](http://ous2s14vo.bkt.clouddn.com/wechatpay_160.jpg) | ![alipay_160](http://ous2s14vo.bkt.clouddn.com/alipay_160.jpg) |

## 支持与讨论

* QQ群:
  * 247451054 [小米PRO黑苹果高级群](http://shang.qq.com/wpa/qunwpa?idkey=6223ea12a7f7efe58d5972d241000dd59cbd0260db2fdede52836ca220f7f20e)
  * 137188006 [小米PRO黑苹果](http://shang.qq.com/wpa/qunwpa?idkey=c17e190b9466a73cf12e8caec36e87124fce9e231a895353ee817e9921fdd74e)

  ​

