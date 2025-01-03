# 系统信息

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/Mac%20Pro.png)


# 配置信息

|              | 硬件配置                        | 备注                                                         |
| ------------ | ------------------------------- | ------------------------------------------------------------ |
| **CPU**      | i5-12600KF                      | Intel 11 代及以上 `CPU 核显` 无法驱动，若读者使用 `12600K` 且在 Windows 下需要使用核显，则需要在 `启动参数` 中添加 `-wegnoigpu` 参数用于在 macOS 下屏蔽核显 |
| **主板**     | MS-Terminator B760M D5          | `MS-Terminator B760M D5 WIFI` 版本仅自带一张 `AX101 无线网卡`，与 `MS-Terminator B760M D5` 无本质区别。<br>理论上 `D5` 是 `MS-Terminator B760M D4` 与 `MS-Terminator B760M D4 WIFI` 的换皮版本，应当也可以使用此配置。<br>由于铭瑄祖传供电与设计方案（一套方案传三代），若有采用与 `D5` 类似的设计方案（如 `板载网卡8125`、`板载声卡 ALC897`）的主板，例如 `MS-iCraft B760M CROSS(未测试)` 应当也可以使用此配置。<br>**注意：此主板(D5)自带网卡接口协议为 `CNVi`，此协议在 macOS 中无法驱动！** |
| **SSD**      | SN570 512G                      | 西部数据： `SN550/570/750/770/850/850X` 对于 `TRIM` 有着完美支持，因此均能正常安装和运行 macOS，建议购买。 |
| **Memory**   | JUHOR 星域 DDR5 6000 16G  * 2    | 颗粒要求：避免矿卡颗粒即可；<br>频率要求：均可；<br>D4 or D5 要求：均可；<br>容量要求：至少 `单根 4G`，否则无法开机。<br>总的来说，没什么特殊要求，除了远古时期的 `AMD 专用内存条` 可能存在问题之外，目前大部分品牌均可。 |
| **显卡**     | 蓝宝石 RX570 8G（免驱卡）       | 或者使用其它免驱卡均可                                       |
| **电源**     | Segotep GM650W 冰川版金牌全模组 | 无特殊要求。<br>注意：A卡 `瞬时功耗` 较高，因此 `5 毛 1 瓦` 以上的电源均可。 |
| **散热**     | Segotep G6                      | 无特殊要求。                                                 |
| **机箱**     | PADO 白泽 360                   | 无特殊要求。                                                 |
| **无线网卡** | BCM943602CS                     | 注意：铭瑄大部分主板网卡接口仅支持 `CNVi` 技术（在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用。 |
| **显示器**   | LQ25F165L                       | 建议 2K 起步，1080P 太辣眼睛啦！                             |
| **键鼠**     | 凑数                            | 无特殊要求，别太烂就行，但最好购买一个双模键盘。 |

***

# 注意事项

## 三码：
  + 读者请使用 [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) 或者 [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools) 生成并修改 `SMBIOS` 中的序列号，以及注入三码
  + **注意：请务必注入三码后再登录 `Apple ID`，否则会被苹果立即拉黑！**
  + **注意：在黑果上登录 `Apple ID` 有拉黑风险，本文档不为此负责！**
## 测试版本
+ 由于 `Sonoma 14.0` 已正式移除了 `IO80211LegacyFamily 驱动`，而为了追求完美体验，本文档仅用于 `macOS 13`，即 `Ventura`。
+ OpenCore 版本：截至本文档编辑时间为 `1.0.1`，读者自己手动同步最新版本即可。
+ macOS 版本：测试版本号为 `13.6.9` （由于 Ventura 已进入维护阶段，因此读者可以自行下载所需的 Ventura 版本）。
## 线材：
  + 在安装 macOS 时，为了不必要的 bug，请使用 DP 线！
## 硬盘：
  + 建议单盘安装 macOS。
  + WD 品牌下的全系列 `SN550/570/580/730/750/770/850/850X` 对于 `TRIM` 有着完美支持，因此均能正常安装和运行 macOS，不会出现 `宕机`, `冻屏` 的现象。
  + 理论上也有一小部分 SSD 完美支持 macOS，但我实在是懒得测试了。
## 网卡：
  + 铭瑄旗下的大部分主板（包括此主板）网卡接口仅支持 `Intel` 的 `CNVi` 协议（而此协议在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用，等到安装完成后可以解除（不影响 win）。
  + `CNVi` 协议可以理解成一个专属通道，其设计目的是消除 `PCIe` 通道占用，提升稳定性和网络速度，降低延迟。但请注意该技术无法在 macOS 里正常工作，也就是说如果主板自带的插槽用仅支持这个技术，那无论是 `英特尔网卡` 或 `博通网卡` 在 macOS 中都无法驱动！
  + 建议购买一张博通免驱卡，例如 `BCM943602CS + PCIe 转接卡`，在某宝中售价仅为 80 元左右?
## 备注：
  + 目前来说，如果想相对完整的体验 `隔空投送`，`接力`，`随航` 等功能，那可能停留在 `Ventura` 是最好的选择了。
  + 由于 `Sonoma 14.0` 及以上的 `macOS 正式版` 已正式移除了 `IO80211LegacyFamily 驱动`，至此所有市面上零售可买到的 `博通拆机网卡` 全部都不再免驱！
  + 虽然可以通过 [OpenCore Legacy Patcher](https://heipg.cn/tag/opencore-legacy-patcher) 找回驱动，那么少年，代价是什么呢？
### 代价
  + 代价：由于目前打补丁方案要求禁用 `AMFI`，因此 `百度网盘`、`天翼云盘` 等基于 `Electron` 的 `APP` 可能无法启动，这类情况虽然可以通过添加启动参 `ipc_control_port_options=0` 解决，but...禁用 `AMFI` 会导致 `Parallels` 免激活版和 `VMware Fusion` 无法正常启动，并且这之后也会有一系列问题在等着你。
  + 以目前的资料来看，如果选择 `Sonoma` 或 `Sequoia`，建议使用 `Intel 网卡（例如 AX210）`，但可能只能使用 `Wi-Fi` 和 `Bluetooth` 功能...
  + 或许，你也可以选择继续折腾？

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
+ VT-x（Intel（VMX）Virtualization Technology）
+ Above 4G Decoding
+ Above 4G MMIO BIOS assignment
+ Hyper-Threading
+ EHCI/XHCI
+ DVMT：256MB

***

# 完善情况

## `1.` Bluetooth and WiFi and 隔空投送

+ 铭瑄大部分主板（包括此主板）网卡接口仅支持 `CNVi` 技术（在 macOS 中无法驱动），建议在安装 macOS 时暂时禁用。

+ 购买的 `BCM943602CS + PCIE 转接卡`，在 `macOS 13`（即 Ventura）中正常使用，支持 `隔空投送` 等功能
  + but...这卡跑不满是正常的
  + `镜像` 这种功能就别想了，毕竟不是白果，没有 T1 / T2 芯片支持

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/all.png)

## `2.` 睡眠

+ 显示器能正常息屏，可通过键鼠唤醒，but...显示器息屏状态下主机还是处于运行状态，属于无解状态
+ 可能是少了核显支持，但毕竟不是白果，做不到那种白果那种睡眠程度

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/电源.png)

## `3.` 图形卡/显示器（没钱买 4K...）

+ HDMI 线只能跑到 144Hz，更高刷新率则需要更换成 DP 线
+ 在安装 macOS 时，为了不必要的 bug，请使用 DP 线

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/显示器.png)

###  `4K 高刷显示器`
使用 DP 接口时，需要关闭显示器的 DSC 功能，否则 DP 口可能会不正常（黑屏、刷新率最高 100Hz 等问题）<br>
解决方案：理论上在关闭后 DSC 功能后，可以正常使用 4K/120Hz/10Bit 输出（无法 HDR），或者使用 4K/95Hz/10Bit（可以使用 HDR），HDMI 接口同样最高支持到 120Hz<br>
注意：
+ 这是 macOS 系统本身的问题！
+ 据说在 （14 后期 / 15）给当 bug 修复了？
+ M1 之后的机型能正常使用 DSC 功能
+ but...都买 M1 了...还黑个锤子...

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/图形卡.png)

## `4.` 板载网卡 and 板载声卡

### 板载网卡：这块板子用的 8125 网卡，驱动正常

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/板载网卡.png)

### 板载声卡：ALC 897，驱动正常，ID 值为12
没声音的请自己手动选择一下音频输出是哪一个，还有目前大部分主板是需要你自己额外购买音响才有声音的！

## `5.` 存储

SN570 512G  西部数据： `SN550/570/750/770/850/850X` 全系列均能正常安装和运行 macOS，建议购买。
  + 理论上也有一小部分 SSD 完美支持 macOS，但我实在是懒得测试了。
  + 例如光威的 `奕系列` ？

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

这一步需要替换至你自己定制的 USB 文件

包括：

+ 主板后置面板：2 个 `USB 3.2`，6个 `USB 2.0`，内置 `Type-C` 接口
  + 板载网卡，板载声卡
  + 注意：
    + 自带无线网卡接口协议为 `CNVi`，此协议在 macOS 中无法驱动！
    + 建议在安装 macOS 时，在 BIOS 中暂时禁用此接口！
    + 在安装完成后可解除！
+ 机箱（ ` 白泽 360 ` ）自带前置面板： 1个 `USB 3.0`，2 个 `USB 2.0` 接口
+ 无线网卡蓝牙等，速率均正常。

不知道咋样叫正常，但我的无线鼠标在 `定制 USB` 后能用，看图

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/USB.png)

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/%E8%93%9D%E7%89%99%20USB%20.png)

***

***

***
# 鸣谢名单（以下排名不分先后）：

苹果公司目前正全力（ M2 Max 之前我还认为可能会跳水 ）转向 `ARM 架构`，毕竟 M4 已经发布了，估计不会回头了(o゜▽゜)o☆
黑果之路已经接近尾声(´。＿。｀)，预计 `Sequoia` 将会是最后一代支持 `X86 架构` 的系统了，但...
是段愉快的旅程 (。・・)ノ


+ 感谢带佬 [JeoJay127](https://github.com/JeoJay127) 无偿分享的工具，本教程的 EFI 基于 [RapidEFI](https://github.com/JeoJay127/RapidEFI-Tool) 工具制作！
+ 感谢 [OpenCore 团队](https://github.com/acidanthera/OpenCorePkg) 制作的内核工具！
+ 感谢 [黑苹果星球](https://heipg.cn/opencore) 提供的参考文档！
+ 感谢 [TerserTop](https://www.bilibili.com/video/BV1eP4y1s76d/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f) 提供的演示教程！
+ 感谢 [win10Q](https://www.bilibili.com/video/BV1ub421J7Lk/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f]) 提供的 `USB 定制` 教程！
+ 感谢 [图拉丁GJ](https://www.bilibili.com/video/BV16p4y1M7G3/?spm_id_from=333.999.0.0&vd_source=259f097c1a5b4870885bbded43057d6f) 提供的 `强刷 VBios` 教程！
+ 感谢 [国光酱](https://apple.sqlsec.com/) 提供的 `国光的黑苹果安装教程：手把手教你配置 OpenCore` 的实战系列教程！
***

***

***

# 附录 Ⅰ · 如果遇到如图所示的错误

![](https://github.com/wenyushu/Maxsun_TERMINATOR_B760M_D5/blob/main/image/52477.jpg)

## 原因（ 详情请参考 `无解硬盘` ）：

黑果这块经常在 NVMe 硬盘这里翻车，比如常见的：三星 `Samsung PM961/PM981/PM981a/PM991` 系列、镁光 `Micron 2200V MTFDHBA512TCK`、`Micron 2200S` 系列等都属于无解状态！
无解是指，在安装 macOS 中必须在 BIOS 中禁用这些无解硬盘（作为 Windows 从盘也不行），否则无法安装 macOS，会卡在如上代码。
并且，如果安装完 macOS 后，还需要设置 SSDT 进行屏蔽，否则也是无法开机进入 macOS  的（会卡在如上代码）！ 


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
