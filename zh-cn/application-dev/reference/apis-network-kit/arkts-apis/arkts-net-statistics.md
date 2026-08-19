# @ohos.net.statistics

流量管理模块提供获取设备网络流量数据的能力。该模块支持从多个维度查询数据包的流量使用情况，例如： - 支持获取指定网卡的上/下行流量数据； - 支持获取所有网卡的总流量数据，便于查看设备整体网络使用情况； - 支持根据应用uid获取指定应用的流量数据，帮助开发者监控应用的网络资源消耗； - 支持获取指定socket的流量统计，为细粒度的网络性能分析提供数据基础； - 支持获取应用在指定时间段内的历史流量使用情况，便于分析应用的长期网络使用趋势。 > **说明：** > > 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 23

<!--Device-unnamed-declare namespace statistics--><!--Device-unnamed-declare namespace statistics-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的下行流量总和(单位:字节)。使用callback异步回调。 |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getSelfTrafficStats](arkts-network-statistics-getselftrafficstats-f.md) | 获取指定时间段内，本应用在指定网络中的流量使用情况。使用Promise异步回调。 |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md) | 获取指定Socket的下行流量（单位：字节）。使用callback异步回调。 |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md) | 获取指定Socket的下行流量（单位：字节）。使用Promise异步回调。 |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md) | 获取指定Socket的上行流量（单位：字节）。使用callback异步回调。 |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md) | 获取指定Socket的上行流量（单位：字节）。使用Promise异步回调。 |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getMonthTrafficStats](arkts-network-statistics-getmonthtrafficstats-f-sys.md) | 获取蜂窝实时下行流量，使用 callback 异步回调。 |
| [getTrafficPlanInfo](arkts-network-statistics-gettrafficplaninfo-f-sys.md) | 获取流量计划信息。 |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md) | 获取指定网卡历史流量信息，使用 callback 异步回调。 |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md) | 获取指定网卡历史流量信息，使用 Promise 异步回调。 \| 参数名 \| 类型 \| 必填 \| 说明 \| \| --------- \| ------------------------- \| ---- \| --------------------------------------------------- \| \| ifaceInfo \| [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) \| 是 \| 指定查询的网卡信息，参见[IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md)。 \| |
| [getTrafficStatsByNetwork](arkts-network-statistics-gettrafficstatsbynetwork-f-sys.md) | 获取指定时间段内所有应用在指定网络中的流量使用详情，使用 Promise 异步回调。 |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md) | 获取指定应用历史流量信息，使用 callback 异步回调。 |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md) | 获取指定应用历史流量信息，使用 Promise 异步回调。 |
| [getTrafficStatsByUidNetwork](arkts-network-statistics-gettrafficstatsbyuidnetwork-f-sys.md) | 获取指定时间段内，应用在指定网络中的流量使用详情，使用 Promise 异步回调。 |
| [offNetStatsChange](arkts-network-statistics-offnetstatschange-f-sys.md) | 取消注册网络流量更新通知。 |
| [off_netStatsChange](arkts-network-statistics-offnetstatschange-f-sys.md) | 取消订阅流量改变事件通知。使用callback异步回调。 |
| [onNetStatsChange](arkts-network-statistics-onnetstatschange-f-sys.md) | 注册网络流量更新通知。 |
| [on_netStatsChange](arkts-network-statistics-onnetstatschange-f-sys.md) | 订阅流量改变事件通知。使用callback异步回调。 |
| [setCalibrationTraffic](arkts-network-statistics-setcalibrationtraffic-f-sys.md) | 设置流量校准数据。在做流量校准时，可通过本接口设置相关流量数据。使用Promise异步回调。 |
| [setTrafficPlanInfo](arkts-network-statistics-settrafficplaninfo-f-sys.md) | 设置流量计划信息。 |
| [updateIfacesStats](arkts-network-statistics-updateifacesstats-f-sys.md) | 更新网络接口统计数据。 |
| [updateStatsData](arkts-network-statistics-updatestatsdata-f-sys.md) | 更新网络统计数据。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) | 查询网卡历史流量参数信息。 |
| [NetStatsChangeInfo](arkts-network-statistics-netstatschangeinfo-i-sys.md) | 监听和管理网络接口的状态和使用情况。 |
| [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) | 获取的历史流量信息。 |
| [NetStatsInfoSequenceItem](arkts-network-statistics-netstatsinfosequenceitem-i-sys.md) | 包含开始时间和结束时间的[NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md)参数。 |
| [NetworkInfo](arkts-network-statistics-networkinfo-i-sys.md) | 网络信息。 |
| [UidInfo](arkts-network-statistics-uidinfo-i-sys.md) | 查询应用历史流量参数信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | 定义与流量计划相关的字段。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetBearType](arkts-network-statistics-netbeartype-t.md) | 网络类型。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NetStatsInfoSequence](arkts-network-statistics-netstatsinfosequence-t-sys.md) | [NetStatsInfoSequenceItem](arkts-network-statistics-netstatsinfosequenceitem-i-sys.md)的数组。 |
| [UidNetStatsInfo](arkts-network-statistics-uidnetstatsinfo-t-sys.md) | [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) for every UID. Key is UID. [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) for every UID. Key is UID. @syscap SystemCapability.Communication.NetManager.Core [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) for every UID. Key is UID. @systemapi Hide this for inner system use. [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) for every UID. Key is UID. @since 12 dynamic [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) for every UID. Key is UID./ export type UidNetStatsInfo = { [uid: int]: NetStatsInfo; }; /** [NetStatsInfo](arkts-network-statistics-netstatsinfo-i-sys.md) for every UID. Key is UID. |
<!--DelEnd-->

