本文列出了 Edge-100 设备的硬件和软件特性。

## 硬件特性
### 基本信息

| 属性         | 规格                                                         |
| ------------ | ------------------------------------------------------------ |
| 产品         | Edge-100                                                     |
| 主处理器     | NXP LS1023A，ARM V8 Cortex A53，2核，1.6GHz。单板硬件设计（供电能力等）兼容平滑升级到 LS1043A，Cortex A53，4 cores，1.6GHz。 |
| 内存         | DDR4，1600MT/S，缺省容量1GB，硬件设计兼容将来升级到2GB和4GB容量。 |
| 存储配置     | <ul><li>BOOTROM NOR Flash，容量为16MB。</li><li>eMMC，8GB。</li><li>EEPROM，2KB 。</li></ul> |
| 时钟         | 支持 RTC 实时时钟，用于记录时间，在设备主电源关断时，该功能仍旧有效，直到纽扣电池耗完为止。 |
| 看门狗       | 支持看门狗功能，当 CPU 宕机时，看门狗电路复位设备，实现故障自动恢复。 |
| 硬件安全设计 | <ul><li>提供存放密钥和证书的安全芯片方案。</li><li>通过安全启动技术，提供防止硬件盗版方案 。</li> </ul> |
| LAN 口       | 3个 GE 电口                                                  |
| WAN 口       | 2个 GE 电口                                                  |
| LTE模组      | LTE 模组支持中国大陆全网通，支持双 APN，M.2。                 |
| Wi-Fi        | Wi-Fi 模组 IEEE 802.11 b/g/n，2x2，miniPCIe 接口。                |
| RJ45         | 一个 RJ45 标准串口，不带指示灯。                                |
| USB          | 一个 USB 2.0 Type-A 接口。                                     |
| SIM          | 1个自弹式 SIM 插槽，机箱上有松脱紧固装置，其中 SIM 卡由腾讯提供。  |
| 指示灯       | <ul><li>电口 RJ-45 自带 LED 指示灯；</li><li>面板绿色指示灯 SYS、POWER、WIFI、LT、蜂窝信号强度1/2/3档 LED，CLOUD 。</li></ul> |
| 天线         | 缺省配置4根天线，其中2根 Wi-Fi 天线，2根 LTE 天线。推荐兼容：2根 Wi-Fi 天线，4根5G天线。 |
| 电源         | 12V电源适配器规格，AC 100~240V @50 - 60 Hz，适配器应已通过 CCC 认证，优选带螺纹紧固插头。 |
| 外型         | 机壳为金属材质，黑色烤漆                                     |
| 认证         | <ul><li>该设备应通过 CCC 认证，SRRC 认证，CTA 认证，RoHS 认证。</li><li>腾讯委托设备供应商完成以上认证（除 RoHS），证书所有者、认证费用承担者均为腾讯。</li><li>RoHS 认证由设备商自行负责。</li></ul> |
| 工作环境     | <ul><li>工作环境温度0°C - 45°C。</li><li>存储温度-40°C - +70°C。</li><li>工作海拔高度小于5000m。</li><li>工作相对湿度5% - 95%，非凝露。</li> </ul> |

### 指示灯说明
>?所有面板灯均为绿色，慢闪表示1s亮1s灭，快闪表示0.5s亮0.5s灭。

| **指示灯名称** | **功能定义**                                                 |
| -------------- | ------------------------------------------------------------ |
| PWR            | 长亮：电源接通<br>熄灭：无电源                               |
| SYS            | 慢闪：正常运行，Edge 控制器可以 ping 通<br>快闪：起始状态，控制器未通<br>长亮：Agent 挂起<br>熄灭：硬件自检故障 |
| WIFI           | 表示 Wi-Fi 连接状态：<br>长亮：WLAN 启动<br>闪烁：数据传输<br>熄灭：WLAN 未启动 |
| LTE/5G         | 长亮：已注册网络<br/>闪烁：数据传输<br/>熄灭：未注册网络     |
| CLOUD          | 表示是否连接到腾讯云：<br/>慢闪：正常工作，已经连接到腾讯云联网<br/>快闪：云网络部分隧道断开或者正在建立连接<br/>长亮：隧道完全断开（已经建立，但后来断开）<br/>熄灭：未开始建立隧道 |
| WAN/LAN        | 表示以太网使用状态：<br>长亮：以太网已连接<br>闪烁：数据传输<br>熄灭：以太网未连接 |


## 软件特性

| 属性                     | 规格                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 操作系统                 | ubuntu 16.04，linux kernel4.14。                               |
| 版本升级                 | <ul><li>支持整个镜像的升级功能，并且升级过程中可撤销。</li><li>升级过程中出现断电等异常场景时，可自动回退到最近可用版本。</li><li>升级过程中，需确保不影响业务配置文件和日志文件，不会出现损坏或者丢失等情况。</li><li>支持手动回退到最近可用的版本。</li> </ul> |
| Wi-Fi 软件特性            | <ul><li>支持 hostapd 进行 Wi-Fi 配置。</li><li>支持多个 ssid。</li> </ul> |
| LTE 软件特性              | <ul><li>支持双 APN（驱动可以支持 ECM 和 ppp 等拨号方式）。</li><li>支持 SIM 卡热插拔。</li> </ul> |
| Reset 按钮对应的软件功能 | <ul><li>支持恢复原始出厂版本。</li><li>支持清空业务配置，即恢复到当前版本的默认配置。</li> </ul> |
| 指示灯管理               | <ul><li>led 灯统一导出到 `/sys/class/leds/ `目录下进行管理，方便应用操作设置，例如：`/sys/class/leds/cloud`，`/sys/class/leds/wifi` 等。</li><li>无法由应用程序控制的 LED（例如 POWER 灯），则统一遵循如下规则：长亮表示正常工作，长暗表示不工作，闪烁表示出现异常。</li> </ul> |
| Kdump 功能               | 将内核宕机详细信息循环覆盖保存到文件系统中。                 |
| 设备管理                 | <ul><li>内存自检告警功能。</li><li>Flash 自检告警功能。</li><li>查看 CPU 当前温度。</li><li>电源电压异常告警。</li><li>网卡相关的操作，例如更改全双工工作模式，更改 ring buffer 大小等等，查看网卡是否异常，查看丢包等异常统计信息等。</li><li>查看 LTE、5G异常信息，包括 SIM 卡是否在位、当前工作模式（飞行模式或正常模式）及天线端接收信号值。</li><li>查看 Wi-Fi 异常信息，包括天线端接收信号值、当前工作频率。</li> <li>检查天线端接收信号值，用于判断天线是否在位。</li> </ul> |
