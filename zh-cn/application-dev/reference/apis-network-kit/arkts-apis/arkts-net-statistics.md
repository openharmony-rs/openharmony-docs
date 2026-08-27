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

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllRxBytes(流量管理)](arkts-network-statistics-getallrxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的下行流量总和(单位:字节)。使用callback异步回调。 |
| [getAllRxBytes(流量管理)](arkts-network-statistics-getallrxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getAllTxBytes(流量管理)](arkts-network-statistics-getalltxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getAllTxBytes(流量管理)](arkts-network-statistics-getalltxbytes-f.md) | 获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getCellularRxBytes(流量管理)](arkts-network-statistics-getcellularrxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getCellularRxBytes(流量管理)](arkts-network-statistics-getcellularrxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getCellularTxBytes(流量管理)](arkts-network-statistics-getcellulartxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getCellularTxBytes(流量管理)](arkts-network-statistics-getcellulartxbytes-f.md) | 获取当前已处于连接状态的蜂窝网络对应的网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getIfaceRxBytes(流量管理)](arkts-network-statistics-getifacerxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getIfaceRxBytes(流量管理)](arkts-network-statistics-getifacerxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getIfaceTxBytes(流量管理)](arkts-network-statistics-getifacetxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getIfaceTxBytes(流量管理)](arkts-network-statistics-getifacetxbytes-f.md) | 获取指定网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |
| [getSelfTrafficStats(流量管理)](arkts-network-statistics-getselftrafficstats-f.md) | 获取指定时间段内，本应用在指定网络中的流量使用情况。使用Promise异步回调。 |
| [getSockfdRxBytes(流量管理)](arkts-network-statistics-getsockfdrxbytes-f.md) | 获取指定Socket的下行流量（单位：字节）。使用callback异步回调。 |
| [getSockfdRxBytes(流量管理)](arkts-network-statistics-getsockfdrxbytes-f.md) | 获取指定Socket的下行流量（单位：字节）。使用Promise异步回调。 |
| [getSockfdTxBytes(流量管理)](arkts-network-statistics-getsockfdtxbytes-f.md) | 获取指定Socket的上行流量（单位：字节）。使用callback异步回调。 |
| [getSockfdTxBytes(流量管理)](arkts-network-statistics-getsockfdtxbytes-f.md) | 获取指定Socket的上行流量（单位：字节）。使用Promise异步回调。 |
| [getUidRxBytes(流量管理)](arkts-network-statistics-getuidrxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用callback异步回调。 |
| [getUidRxBytes(流量管理)](arkts-network-statistics-getuidrxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的下行流量总和（单位：字节）。使用Promise异步回调。 |
| [getUidTxBytes(流量管理)](arkts-network-statistics-getuidtxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。 |
| [getUidTxBytes(流量管理)](arkts-network-statistics-getuidtxbytes-f.md) | 获取指定应用从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getMonthTrafficStats(流量管理)](arkts-network-statistics-getmonthtrafficstats-f-sys.md) | 获取蜂窝实时下行流量，使用 callback 异步回调。 |
| [getTrafficPlanInfo(流量管理)](arkts-network-statistics-gettrafficplaninfo-f-sys.md) | 获取流量计划信息。 |
| [getTrafficStatsByIface(流量管理)](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md) | 获取指定网卡历史流量信息，使用 callback 异步回调。 |
| [getTrafficStatsByIface(流量管理)](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md) | 获取指定网卡历史流量信息，使用 Promise 异步回调。  \| 参数名 \| 类型 \| 必填 \| 说明 \| \| --------- \| ------------------------- \| ---- \| --------------------------------------------------- \| \| ifaceInfo \| [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) \| 是 \| 指定查询的网卡信息，参见[IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md)。 \| |
| [getTrafficStatsByNetwork(流量管理)](arkts-network-statistics-gettrafficstatsbynetwork-f-sys.md) | 获取指定时间段内所有应用在指定网络中的流量使用详情，使用 Promise 异步回调。 |
| [getTrafficStatsByUid(流量管理)](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md) | 获取指定应用历史流量信息，使用 callback 异步回调。 |
| [getTrafficStatsByUid(流量管理)](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md) | 获取指定应用历史流量信息，使用 Promise 异步回调。 |
| [getTrafficStatsByUidNetwork(流量管理)](arkts-network-statistics-gettrafficstatsbyuidnetwork-f-sys.md) | 获取指定时间段内，应用在指定网络中的流量使用详情，使用 Promise 异步回调。 |
| off(流量管理) | 取消订阅流量改变事件通知。使用callback异步回调。 |
| on(流量管理) | 订阅流量改变事件通知。使用callback异步回调。 |
| [setCalibrationTraffic(流量管理)](arkts-network-statistics-setcalibrationtraffic-f-sys.md) | 设置流量校准数据。在做流量校准时，可通过本接口设置相关流量数据。使用Promise异步回调。 |
| [setTrafficPlanInfo(流量管理)](arkts-network-statistics-settrafficplaninfo-f-sys.md) | 设置流量计划信息。 |
| [updateIfacesStats(流量管理)](arkts-network-statistics-updateifacesstats-f-sys.md) | 更新网络接口统计数据。 |
| [updateStatsData(流量管理)](arkts-network-statistics-updatestatsdata-f-sys.md) | 更新网络统计数据。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [NetStatsInfo(流量管理)](arkts-network-statistics-netstatsinfo-i.md) | 获取的历史流量信息。 |
| [NetworkInfo(流量管理)](arkts-network-statistics-networkinfo-i.md) | 网络信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IfaceInfo(流量管理)](arkts-network-statistics-ifaceinfo-i-sys.md) | 查询网卡历史流量参数信息。 |
| [NetStatsChangeInfo(流量管理)](arkts-network-statistics-netstatschangeinfo-i-sys.md) | 监听和管理网络接口的状态和使用情况。 |
| [UidInfo(流量管理)](arkts-network-statistics-uidinfo-i-sys.md) | 查询应用历史流量参数信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TrafficPlanParam(流量管理)](arkts-network-statistics-trafficplanparam-e-sys.md) | 定义与流量计划相关的字段。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetBearType(流量管理)](arkts-network-statistics-netbeartype-t.md) | 网络类型。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UidNetStatsInfo(流量管理)](arkts-network-statistics-uidnetstatsinfo-t-sys.md) | [NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md) for every UID. Key is UID. [NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md) for every UID. Key is UID. |
<!--DelEnd-->
