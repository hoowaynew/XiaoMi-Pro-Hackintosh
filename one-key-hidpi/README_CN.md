# 开启macOS HiDPI

[English](README.md) | 中文

## 简介

此脚本的目的是为中低分辨率的屏幕开启 HiDPI 选项，并且具有原生的 HiDPI 设置，不需要 RDM 软件即可在系统显示器设置中设置。开启后分辨率会伪装成2848 x 1604，UI看起来像1424 x 802。相比之前的版本，这个脚本解决了开机花屏和唤醒花屏问题。

macOS 的 DPI 机制和 Windows 下不一样，比如 1080p 的屏幕在 Windows 下有 125%、150% 这样的缩放选项，而同样的屏幕在 macOS 下，缩放选项里只是单纯的调节分辨率，这就使得在默认分辨率下字体和UI看起来很小，降低分辨率又显得模糊。

开机的第二阶段 logo 总是会稍微放大，因为分辨率是仿冒的。

目录里的脚本为小米笔记本Pro专用。


## 使用方法

- 在终端输入以下命令并回车：
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/daliansky/XiaoMi-Pro-Hackintosh/master/one-key-hidpi/one-key-hidpi_cn.sh)"
```

- macOS 10.14或以上，你可能需要开启次像素抗锯齿来获得更好的体验
 - 在终端输入以下命令并回车：
 ```bash
defaults write -g CGFontRenderingFontSmoothingDisabled -bool NO
```

 - 然后调整抗锯齿的配置：
  - 最强级别
```bash
defaults -currentHost write -globalDomain AppleFontSmoothing -int 3
```
  - 中等级别
```bash
defaults -currentHost write -globalDomain AppleFontSmoothing -int 2
```
  - 轻微级别
```bash
defaults -currentHost write -globalDomain AppleFontSmoothing -int 1
```


## 恢复

如果使用此脚本后，开机无法进入系统，请到恢复模式中或使用 clover `-x` 安全模式进入系统 ，使用终端删除 `/System/Library/Displays/Contents/Resources/Overrides` 下删除 `DisplayVendorID-9e5` 文件夹，并把 backup 文件夹中的备份复制出来。

具体命令如下：
```
$ cd /Volumes/你的系统盘/System/Library/Displays/Contents/Resources/Overrides
$ rm -rf ./DisplayVendorID-9e5
$ cp -r ./backup/* ./
```

如果要回滚次像素抗锯齿设置，在终端输入以下命令并回车：
```bash
defaults -currentHost delete -globalDomain AppleFontSmoothing
```
和：
```bash
defaults write -g CGFontRenderingFontSmoothingDisabled -bool YES
```


## 鸣谢

- 感谢[xzhih](https://github.com/xzhih) 提供界面。
    - 父级脚本: [one-key-hidpi](https://github.com/xzhih/one-key-hidpi)
- 感谢 [zysuper](https://github.com/zysuper) 提供分辨率。
