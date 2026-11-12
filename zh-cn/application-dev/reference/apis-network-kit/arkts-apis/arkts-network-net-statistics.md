# @ohos.net.statistics(流量管理)

流量管理模块提供获取设备网络流量数据的能力。该模块支持从多个维度查询数据包的流量使用情况，例如：

- 支持获取指定网卡的上/下行流量数据；  
- 支持获取所有网卡的总流量数据，便于查看设备整体网络使用情况；  
- 支持根据应用uid获取指定应用的流量数据，帮助开发者监控应用的网络资源消耗；  
- 支持获取指定socket的流量统计，为细粒度的网络性能分析提供数据基础；  
- 支持获取应用在指定时间段内的历史流量使用情况，便于分析应用的长期网络使用趋势。

> **说明：** 
> 
> 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 10

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
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md#getallrxbytes-1) | 获取所有网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md#getallrxbytes-2) | 获取所有网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md#getalltxbytes-1) | 获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md#getalltxbytes-2) | 获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md#getcellularrxbytes-1) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md#getcellularrxbytes-2) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md#getcellulartxbytes-1) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md#getcellulartxbytes-2) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md#getifacerxbytes-1) | 获取指定网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md#getifacerxbytes-2) | 获取指定网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md#getifacetxbytes-1) | 获取指定网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md#getifacetxbytes-2) | 获取指定网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getSelfTrafficStats](arkts-network-statistics-getselftrafficstats-f.md#getselftrafficstats-1) | 获取指定时间段内，本应用在指定网络中的流量使用情况。使用Promise异步回调。 |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md#getsockfdrxbytes-1) | 获取指定Socket的下行流量（单位：字节）。使用callback异步回调。 |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md#getsockfdrxbytes-2) | 获取指定Socket的下行流量（单位：字节）。使用Promise异步回调。 |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md#getsockfdtxbytes-1) | 获取指定Socket的上行流量（单位：字节）。使用callback异步回调。 |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md#getsockfdtxbytes-2) | 获取指定Socket的上行流量（单位：字节）。使用Promise异步回调。 |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md#getuidrxbytes-1) | 获取指定应用从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md#getuidrxbytes-2) | 获取指定应用从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md#getuidtxbytes-1) | 获取指定应用从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md#getuidtxbytes-2) | 获取指定应用从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getMonthTrafficStats](arkts-network-statistics-getmonthtrafficstats-f-sys.md#getmonthtrafficstats-1) | 获取蜂窝实时下行流量，使用 callback 异步回调。 |
| [getTrafficPlanInfo](arkts-network-statistics-gettrafficplaninfo-f-sys.md#gettrafficplaninfo-1) | 获取流量计划信息。 |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md#gettrafficstatsbyiface-1) | 获取指定网卡历史流量信息，使用callback异步回调。系统根据ifaceInfo中指定的网卡名和时间范围，从流量统计数据库中读取该网卡在对应时间段内的收发字节数与包数，通过回调返回；若网卡名无效或该时间段内无统计数据，则返回全零的统计信息。 |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md#gettrafficstatsbyiface-2) | 获取指定网卡历史流量信息，使用Promise异步回调。系统根据ifaceInfo中指定的网卡名和时间范围，从流量统计数据库中读取该网卡在对应时间段内的收发字节数与包数并以Promise形式返回；若网卡名无效或该时间段内无统计数据，则返回全零的统计信息。 |
| [getTrafficStatsByNetwork](arkts-network-statistics-gettrafficstatsbynetwork-f-sys.md#gettrafficstatsbynetwork-1) | 获取指定时间段内所有应用在指定网络中的流量使用详情，使用Promise异步回调。系统根据networkInfo中的网络类型、时间范围及simId，从流量统计数据库中聚合该网络下各应用（按uid维度）的历史流量数据并以Promise形式返回UidNetStatsInfo；其中simId仅在网络类型为蜂窝网络（BEARER_CELLULAR）时生效。 |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md#gettrafficstatsbyuid-1) | 获取指定应用历史流量信息，使用callback异步回调。系统根据uidInfo中指定的应用uid及网卡、时间范围，从流量统计数据库中读取该应用在对应时间段内的收发字节数与包数，通过回调返回；若该应用在指定时间段内无流量记录，则返回全零的统计信息。 |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md#gettrafficstatsbyuid-2) | 获取指定应用历史流量信息，使用Promise异步回调。系统根据uidInfo中指定的应用uid及网卡、时间范围，从流量统计数据库中读取该应用在对应时间段内的收发字节数与包数并以Promise形式返回；若该应用在指定时间段内无流量记录，则返回全零的统计信息。 |
| [getTrafficStatsByUidNetwork](arkts-network-statistics-gettrafficstatsbyuidnetwork-f-sys.md#gettrafficstatsbyuidnetwork-1) | 获取指定时间段内，应用在指定网络中的流量使用详情，使用Promise异步回调。系统根据uid及networkInfo中的网络类型、时间范围、simId，从流量统计数据库中读取该应用在指定网络下的历史流量数据，按时间段返回NetStatsInfoSequence序列并以Promise形式返回；其中simId仅在网络类型为蜂窝网络（BEARER_CELLULAR）时生效。 |
| [off('netStatsChange')](arkts-network-statistics-off-f-sys.md#offnetstatschange) | 取消订阅流量改变事件通知。使用callback异步回调。 |
| [on('netStatsChange')](arkts-network-statistics-on-f-sys.md#onnetstatschange) | 订阅流量改变事件通知。使用callback异步回调。 |
| [setCalibrationTraffic](arkts-network-statistics-setcalibrationtraffic-f-sys.md#setcalibrationtraffic-1) | 设置流量校准数据。在做流量校准时，可通过本接口设置相关流量数据，接口会将simId对应的剩余流量（remainTraffic）与套餐总流量（totalTraffic）写入系统流量统计数据库并用于后续流量统计与校准计算，校准结果对后续查询接口返回的数据生效。使用Promise异步回调。 |
| [setTrafficPlanInfo](arkts-network-statistics-settrafficplaninfo-f-sys.md#settrafficplaninfo-1) | 设置流量计划信息。 |
| [updateIfacesStats](arkts-network-statistics-updateifacesstats-f-sys.md#updateifacesstats-1) | 更新网络接口统计数据。 |
| [updateStatsData](arkts-network-statistics-updatestatsdata-f-sys.md#updatestatsdata-1) | 更新网络统计数据。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md) | 获取的历史流量信息。 |
| [NetworkInfo](arkts-network-statistics-networkinfo-i.md) | 网络信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) | 查询网卡历史流量参数信息。 |
| [NetStatsChangeInfo](arkts-network-statistics-netstatschangeinfo-i-sys.md) | 流量变化事件上报的网卡名称及应用UID等信息。 |
| [UidInfo](arkts-network-statistics-uidinfo-i-sys.md) | 查询应用历史流量参数信息。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetBearType](arkts-network-statistics-netbeartype-t.md) | 网络类型。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UidNetStatsInfo](arkts-network-statistics-uidnetstatsinfo-t-sys.md) | 获取的所有应用历史流量信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | 定义与流量计划相关的字段。 |
<!--DelEnd-->
