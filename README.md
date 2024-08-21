# 系统信息

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/Mac%20Pro.png)


# 配置信息

|              | 硬件配置                        | 备注                                                         |
| ------------ | ------------------------------- | ------------------------------------------------------------ |
| **CPU**      | i5-12600KF                      | Intel 11代及以上 `CPU` 核显无法驱动，若读者使用 `12600K` 且在 Windows 下需要使用核显，则需要在 `启动参数` 中添加 `-wegnoigpu` 参数用于在 macOS 下屏蔽核显 |
| **主板**     | MS-Terminator B760M D5          | `MS-Terminator B760M D5 WIFI` 版本仅自带一张 `AX101 无线网卡`，与 `MS-Terminator B760M D5` 无本质区别。<br>理论上为 `D5` 是 `MS-Terminator B760M D4` 与 ``MS-Terminator B760M D4 WIFI` 的换皮版本，应当可以使用此配置。<br>由于铭瑄祖传供电与设计方案（一套方案传三代），若有采用与 `D5` 类似的设计方案（如 `板载网卡8125`、`板载声卡 ALC897`）的主板，例如 `MS-iCraft B760M CROSS(未测试)` 应当也可以使用此配置。<br>**注意：此主板自带网卡接口协议为 `CNVi`，此协议在 macOS 中无法驱动！** |
| **SSD**      | SN570 512G                      | 西部数据： `SN550/570/750/770/850/850X` 对于 `TRIM` 有着完美支持，因此均能正常安装和运行 macOS，建议购买。 |
| **Memory**   | JUHOR 星域 DDR5 6000 16G  * 2    | 颗粒要求：避免矿卡颗粒即可；频率要求：均可；D4 or D5 要求：均可；容量要求：至少 `单根 4G`，否则无法开机。<br>没什么特殊要求，除了远古时期的 `AMD 专用内存条` 可能存在问题之外，目前大部分品牌均可。 |
| **显卡**     | 蓝宝石 RX570 8G（免驱卡）       | 或者使用其它免驱卡均可                                       |
| **电源**     | Segotep GM650W 冰川版金牌全模组 | 无特殊要求。<br>注意：A卡 `瞬时功耗` 较高，因此 `5 毛 1 瓦` 以上的电源均可。 |
| **散热**     | Segotep G6                      | 无特殊要求。                                                 |
| **机箱**     | PADO 白泽 360                   | 无特殊要求。                                                 |
| **无线网卡** | BCM943602CS                     | 注意：铭瑄大部分主板网卡接口仅支持 `CNVi` 技术（在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用。 |
| **显示器**   | LQ25F165L                       | 建议 2K 起步，1080P 太辣眼睛啦！                             |
| **键鼠**     | 凑数                            | 无特殊要求，别太烂就行，但最好购买一个双模键盘。 |

***

# 注意事项

+ 三码：
  + 读者请使用 [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) 或者 [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools) 生成并修改 `SMBIOS` 中的序列号，以及注入三码
  + **注意：请务必注入三码后再登录 `Apple ID`，否则会被苹果立即拉黑！**
  + **注意：在黑果上登录 `Apple ID` 有拉黑风险，本文档不为此负责！**
  
+ 由于 `Sonoma 14.0` 已正式移除了 `IO80211LegacyFamily 驱动`，而为了追求完美体验，本文档仅用于 `macOS 13`，即 `Ventura` 版本。
+ OpenCore 版本：截至本文档编辑时间为 `1.0.1`。
+ macOS 版本：测试版本号为 `13.6.9`。
+ 线材：
  + 在安装 macOS 时，为了不必要的 bug，请使用 DP 线！
+ 硬盘：
  + 建议单盘安装 macOS。
  + WD 品牌下的全系列 `SN550/570/580/730/750/770/850/850X` 对于 `TRIM` 有着完美支持，因此均能正常安装和运行 macOS，不会出现 `宕机`, `冻屏` 的现象。
+ 网卡：
  + 铭瑄大部分主板（包括此主板）网卡接口仅支持 `CNVi` 协议（而此协议在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用，等到安装完成后可以解除。
  + 建议购买一张博通免驱卡，例如 `BCM943602CS` + `PCIE 转接卡`，在某宝中售价仅为 90 元左右！
***

# BIOS 设置

### 禁用：

+ Fast Boot
+ Secure Boot
+ VT-d
+ CSM
+ CFG Lock

### 开启：

+ XMP
+ VT-x
+ Above 4G decoding
+ Intel（VMX）Virtualization Technology
+ Hyper-Threading
+ EHCI/XHCI
+ DVMT：32MB 或更高

***

# 完善情况

## `1.` Bluetooth and WiFi and 隔空投送

+ 铭瑄大部分主板（包括此主板）网卡接口仅支持 `CNVi` 技术（在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用。

+ 购买的 `BCM943602CS` + `PCIE 转接卡`，在 macOS 13（即 `Ventura` 版本）中正常使用，支持 `隔空投送` 等功能。
  + but...这卡跑不满是正常的

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/all.png)

## `2.` 睡眠

显示器能正常息屏，可通过键鼠唤醒，but...显示器息屏状态下主机还是处于运行状态，属于无解状态

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/电源.png)

## `3.` 图形卡/显示器（没钱买 4K...）

+ HDMI 线只能跑到 144Hz，更高刷新率则需要更换成 DP 线
+ 在安装 macOS 时，为了不必要的 bug，请使用 DP 线

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/显示器.png)

###  `4K 高刷显示器`
使用 DP 接口时，需要关闭显示器的 DSC 功能，否则 DP 口可能会不正常（黑屏、刷新率最高 100Hz 等问题），注意：这是 MacOS 系统本身的问题。
+ 因此，理论上在关闭后 DP 接口后，可以正常使用 4K/120Hz/10Bit 输出（无法 HDR），或者使用 4K/95Hz/10Bit（可以使用 HDR）
  + HDMI 接口同样最高支持到 120Hz
+ 目前只有 M1 之后的机型才能正常使用 DSC
  + 都买 M1 了...还黑个锤子...

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/图形卡.png)

## `4.` 板载网卡 and 板载声卡

### 板载网卡：这块板子用的 8125 网卡，驱动正常

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/板载网卡.png)

### 板载声卡：ALC 897，驱动正常，ID 值为12

## `5.` 存储

SN570 512G  西部数据： `SN550/570/750/770/850/850X` 全系列均能正常安装和运行 macOS，建议购买。

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/存储.png)

## `6.` Memory

+ 没什么特殊要求，除了远古时期的 `AMD 专用内存条` 可能存在问题之外，目前大部分品牌均可。
  + 颗粒：避免垃圾颗粒
  + 频率：均可
  + D4 and D5：均可
  + 容量：至少 `单根 4G`，否则无法开机

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/内存.png)

***

# USB 定制部分

包括：

+ 主板后置面板：2 个 `USB 3.2`，6个 `USB 2.0`，内置 `Type-C` 接口
  + 板载网卡，板载声卡
  + 注意：自带无线网卡接口协议为 `CNVi`，此协议在 macOS 中无法驱动！建议在安装 macOS 时，在 BIOS 中暂时禁用此接口！在安装完成后可解除！
+ 机箱（ ` 白泽 360 ` ）自带前置面板： 1个 `USB 3.0`，2 个 `USB 2.0` 接口
+ 无线网卡蓝牙等，速率均正常。

不知道咋样叫正常，但我的无线鼠标在 `定制 USB` 后能用，看图

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/USB.png)

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/%E8%93%9D%E7%89%99%20USB%20.png)

***

***

***
# 鸣谢名单（以下排名不分先后）：

+ 感谢带佬 [JeoJay127](https://github.com/JeoJay127) 无偿分享的工具，本教程的 EFI 基于 [RapidEFI](https://github.com/JeoJay127/RapidEFI-Tool) 工具制作！
+ 感谢 [OpenCore 团队](https://github.com/acidanthera/OpenCorePkg) 制作的内核工具！
+ 感谢 [黑苹果星球](https://heipg.cn/opencore) 提供的参考文档！
+ 感谢 [TerserTop](https://www.bilibili.com/video/BV1eP4y1s76d/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f) 提供的演示教程！
+ 感谢 [win10Q](https://www.bilibili.com/video/BV1ub421J7Lk/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f]) 提供的 `USB 定制` 教程！
+ 感谢 [图拉丁GJ](https://www.bilibili.com/video/BV16p4y1M7G3/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f) 提供的 `强刷 VBios` 教程！
+ 感谢 [大头蔡Cass](https://www.bilibili.com/video/BV17e4y1A7os/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f) 提供的注意事项！
+ 感谢 [国光酱](https://apple.sqlsec.com/) 提供的 `国光的黑苹果安装教程：手把手教你配置 OpenCore` 的实战系列教程！
***

***

***

# 附录 Ⅰ · 如果遇到如图所示的错误

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/52477.jpg)

## 原因（ 详情请参考 `无解硬盘` ）：

黑果这块经常在 NVME 硬盘这里翻车，比如常见的：三星 `Samsung PM961/PM981/PM981a/PM991` 系列、镁光 `Micron 2200V MTFDHBA512TCK`、`Micron 2200S` 系列等！

而本文档的计算机中装有三块 `NVMe` 的 `SSD`，并且打算将 macOS 安装到第三块西数 `SN570` 的硬盘中，如下所示：

+ 第一块为：`GLOWAY YCT512NVMe-M.2`
+ 第二块为：`Micron MTFDHBA1T0TCK`，这块硬盘对于 macOS 无解，因此会出现如上报错！
+ 第三块为：`WD Blue SN570 500GB`

## 解决办法如下（ 临时，仅用于安装 macOS ）：

+ 进入 `BIOS` -> `Advanced` -> `Nvme Configuration`

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/nvem_configuration.jpg)

+ 仅保留所需要安装的硬盘，例如本文档将 macOS 安装到 `SN570` SSD 中
  + 则需要将其它 SSD 设置成禁用状态！
  + macOS 安装完成，并设置好引导后，再做调整！

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/nvme.jpg)

## 解决办法 - PXPX 方法（ 永久 ）
为了避免重复造轮子，详情请参考 [国光酱 - 屏蔽不支持的硬盘 ](https://apple.sqlsec.com/6-%E5%AE%9E%E7%94%A8%E5%A7%BF%E5%8A%BF/6-8.html)
