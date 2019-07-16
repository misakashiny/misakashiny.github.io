---
layout: post
title: Redmi NOTE4刷机汇总
date: 2018-05-03 05:07:07
tags: 刷机
---
一些ROM的网站收集

数据无价，请多备份
<!--more-->
----------
>魔趣--[`官方链接`](http://www.mokeedev.com/)
>
易用、流畅、省电的原生风格ROM

<p>

> omni [`官方下载链接`](https://dl.omnirom.org/mido/)
>
Android原生系统,基于LineageOS系统

<p>

> Resurrection Remix OS[`官方下载链接`](http://www.resurrectionremix.com/)
>
我们致力于让您的Android体验更加优雅，精心挑选的功能包含在一个操作系统中。

<p>

>LineageOS--[`官方链接`](https://www.lineageos.org/)
>
LineageOS是基于Android移动平台的智能手机和平板电脑的免费开源操作系统。

<p>

>AOSP extended(AEX)--[`官方链接`](https://www.aospextended.com/)
>
AOSP Extended是一个基于AOSP的ROM，它提供了具有各种定制功能
以及底层主题引擎的库存UI / UX。

<p>

>SlimRoms--[`官方链接`](https://slimroms.org/)
>
Slim是一款定制的android操作系统，我们的主要目标是为用户提供简便
但仍然具有丰富的替代其他Android操作系统的功能。

<p>

>Android Ice Cold Project(AICP)--[`官方链接`](http://aicp-rom.com/)
>
官方并没有说明自己是什么类型

<p>

>SudaMod--[`官方链接`](https://sudamod.download/)
>
致力于打造纯净的安卓本土化系统

<p>

#  >  Google全家桶#
----------

Open Gapps--[官方链接](https://opengapps.org/)

版本问题嘛，Github上的WIKI有详细对比，更具自己的需求下载（通常使用pico）

Package 比较 WIKI:[点此链接查看](https://github.com/opengapps/opengapps/wiki/Package-Comparison)

# >  ROOT管理员权限 #
----------
SuperSU--[官方链接](http://www.supersu.com/)

Magisk Manager--[官方链接](https://magiskmanager.com/)


# >  adb Shell批量安装APP #
----------
◉准备工作：

ADB工具包:[点击此处下载](http://adbshell.com/downloads)

打开你的安卓设备里的USB调试模式

重命名APK（APK文件名中不能有中文、特殊符号）

把你的APK放到ADB目录里

◉cmd里面输入

	adb shell-------激活ADB服务

	adb devices-------检查可发现设备

	安装ADB目录下的全部安装包：

	for %i in (*.apk) do adb install %i

# >Fastboot刷入Recovery #

----------
> 可能需要Fastboot工具包的支持

> 进入Bootloader
> CMD中输入```` fastboot devices -l ```` (若回馈一串序列号，说明设备已连接)

> 刷入Recovery
> fastboot flash recovery (Rec文件地址)

# >  一些实质性的东西 #

----------

XDA--[官方链接](https://www.xda-developers.com/)

TWRP--[官方链接](https://magiskmanager.com/)

# >  常见错误解决方法 #
### 机型验证：E3004 ###

>这种情况一般都是ROM自带的机型验证导致的，若是确定该ROM包可以支持你的设备的话，删除机型验证即可

> 打开ROM内的  ````updater-script````   文件（ 用 Notepad++ 打开 ）
删除
assert(getprop("ro.product.device") == "该ROM机型" || getprop("ro.build.product") == "该ROM机型" || abort("E3004: This package is for device: mido; this device is " + getprop("ro.product.device") + "."););
然后保存即可

### 更新System镜像失败：E1001 ###

> 尝试一下清除System分区再刷ROM，若是不行的话一般就是ROM损坏导致的，刷ROM前建议检查一下文件的完整性

### TrustZone版本不符 ###

> 该ROM对TrustZone版本有要求，请更新底包(Firmware)。一般来说用同Android版本最新的底包即可，部分ROM可能有特殊要求

> 错误的底包版本会导致各种bug，如Home键、指纹失灵、

### system分区空间不够 ###

> 这是由于系统分区空间不够造成的
> 可以尝试使用以下的方法解决
>     
> 减少需要刷入的内容
>  删除一些system分区的东西以释放空间
> 使用Magisk将相关内容安装到system分区外(GApps也可以)