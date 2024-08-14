[铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.md](https://github.com/user-attachments/files/16614404/B760M.D5.opencore.EFI.md)
# Maxsun_TERMINATOR_B760M_D5
# 系统信息

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/MacPro.png)


# 配置信息

|              | 硬件配置                        | 备注                                                         |
| ------------ | ------------------------------- | ------------------------------------------------------------ |
| **CPU**      | i5-12600KF                      | 11代及以上 `CPU` 核显无法驱动，若读者使用 `12600K` 则需要添加 参数屏蔽核显 |
| **主板**     | MS-Terminator B760M D5          | `MS-Terminator B760M D5 WIFI` 版本仅自带一张 `无线网卡`，与 `MS-Terminator B760M D5` 无本质区别。<br>理论上 `MS-Terminator B760M D4` 与 ``MS-Terminator B760M D4 WIFI` 为 `D5` 换皮版本，应当可以使用此配置。<br>由于铭瑄经常祖传供电与设计方案（一套方案传三代），若有采用与 `D5` 类似的设计方案（如 `板载网卡8125`、`板载声卡 ALC897`）的主板，例如 `MS-iCraft B760M CROSS(未测试)` 应当也可以使用此配置。<br>**注意：自带网卡接口协议为 `CNVi`，无法驱动！** |
| **SSD**      | SN570 512G                      | 西部数据： `SN550/570/750/770/850/850X` 均能正常安装和运行 macOS，建议购买。 |
| **Memory**   | JUHOR 星域DDR5 6000 16G  * 2    | 没什么特殊要求，除了远古时期的 `AMD 专用内存条` 可能存在问题之外，目前大部分品牌均可。<br>颗粒：避免垃圾颗粒；频率：均可；D4 and D5：均可；容量：至少 `单根 4G`，否则无法开机。 |
| **显卡**     | 蓝宝石 RX570 8G（免驱卡）       | 或者使用其它免驱卡均可                                       |
| **电源**     | Segotep GM650W 冰川版金牌全模组 | 无特殊要求。<br>注意：A卡 `瞬时功耗` 较高，因此 6 毛 1 瓦 以上的电源均可。 |
| **散热**     | Segotep G6                      | 无特殊要求。                                                 |
| **机箱**     | PADO 白泽 360                   | 无特殊要求。                                                 |
| **无线网卡** | BCM943602CS                     | 注意：铭瑄大部分主板网卡接口仅支持 `CNVi` 技术（在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用。 |
| **显示器**   | LQ25F165L                       | 建议 2K 起步，1080P 太辣眼睛啦！                             |
| **键鼠**     | 凑数                            |                                                              |

***

# 注意事项

+ 读者请使用 [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) 或者 [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools) 生成并修改 `SMBIOS` 中的序列号，以及注入三码
  + 注意：请务必注入三码后再登录 ID，否则会被苹果拉黑！
+ 由于 `Sonoma 14.0` 已正式移除了 `IO80211LegacyFamily 驱动`，而为了追求完美体验，本文档仅用于 `macOS 13`，即 `Ventura` 版本
+ OpenCore 版本：截至本文档编辑时间为 `1.0.1`
+ macOS 版本：测试平台为 `13.6.9`
+ 在安装 macOS 时，为了不必要的 bug，请使用 DP 线
+ 建议单盘安装 macOS

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

+ 铭瑄大部分主板网卡接口仅支持 `CNVi` 技术（在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用。

+ 购买的 `BCM943602CS 转接 PCIE`，在 macOS 13（即 `Ventura` 版本）中正常使用，支持 `隔空投送` 等功能。
  + but...这卡跑不满是正常的

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/all.png)

## `2.` 睡眠

显示器能正常息屏，可通过键鼠唤醒

but...显示器息屏状态下主机还是处于运行状态，属于无解状态

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/电源.png)

## `3.` 图形卡/显示器（没钱买 4K...）

+ HDMI 线只能跑到 144Hz，更高刷新率则需要更换成 DP 线
+ 在安装 macOS 时，为了不必要的 bug，请使用 DP 线

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/显示器.png)

+ 在 4K 高刷显示器下，使用 DP 接口需要关闭显示器的 DSC 功能，否则 DP 口可能会不正常（黑屏、刷新率最高 100Hz 等问题），注意这是 MacOS 系统本身的问题。
  + 关闭后 DP 口可以正常使用 4K/120Hz/10Bit 输出（无法 HDR）或是 4K95Hz10Bit（可以使用 HDR）
  + HDMI 接口同样最高 120Hz
+ 目前只有 M1 之后的机型才能正常使用 DSC
  + 都买 M1 了...还黑个锤子...

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/图形卡.png)

## `4.` 板载网卡 and 板载声卡

### 板载网卡：这块板子用的 8125 网卡，驱动正常

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/板载网卡.png)

### 板载声卡：ALC 897，驱动正常，ID 为12

## `5.` 存储

SN570 512G  西部数据： `SN550/570/750/770/850/850X` 均能正常安装和运行 macOS，建议购买。

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/存储.png)

## `6.` Memory

+ 没什么特殊要求，除了远古时期的 `AMD 专用内存条` 可能存在问题之外，目前大部分品牌均可。
  + 颗粒：避免垃圾颗粒
  + 频率：均可
  + D4 and D5：均可
  + 容量：至少 `单根 4G`，否则无法开机

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/内存.png)

***

# USB 定制部分

包括：

+ 主板后置面板：2 个 USB 3.2，6个 USB 2.0，Type-C 接口
  + 板载网卡，板载声卡
  + 注意：自带无线网卡接口协议为 `CNVi`，无法驱动！建议在安装 macOS 时在 BIOS 中暂时禁用此接口！
+ 机箱自带前置面板： 1个 USB 3.0，2 个 USB 2.0 接口
+ 无线网卡蓝牙等，速率均正常。

不知道咋样叫正常，但我的无线鼠标在 `定制USB` 后能用，看图

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/USB.png)

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/蓝牙 USB .png)

***

***

***

# 附录 Ⅰ · 如果遇到如图所示的错误

![52477](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/52477.jpg)

### 解决办法如下：

本文档的计算机中装有三块 `NVMe` 的 `SSD`，并且打算将 macOS 安装到第三块西数 SN570 的硬盘中

+ 进入 `BIOS` -> `Advanced` -> `Nvme Configuration`

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/nvem_configuration.jpg)

+ 仅保留所需要安装的硬盘，例如本文档将 macOS 安装到 SN570 SSD 中
  + 则需要将其它 SSD 设置成禁用状态
  + macOS 安装完成，并设置好引导后，可解除禁用

![](铭瑄 B760M 终结者 D5 opencore 配置分享 EFI.assets/nvme.jpg)
