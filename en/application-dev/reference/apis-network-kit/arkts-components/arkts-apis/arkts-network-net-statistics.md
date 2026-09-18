# @ohos.net.statistics(Traffic Management)

The Traffic Management module provides the capability to obtain device network traffic data. This module supports querying packet traffic usage from multiple dimensions, for example:

- Obtaining the uplink/downlink traffic data of a specified NIC.  
- Obtaining the total traffic data of all NICs, facilitating the viewing of overall device network usage.  
- Obtaining the traffic data of a specified application based on the application UID, helping you monitor the network  
resource consumption of applications.  
- Obtaining traffic statistics for a specified socket, providing a data foundation for fine-grained network  
performance analysis.  
- Obtaining the historical traffic usage of an application within a specified time period, facilitating the analysis  
of long-term network usage trends of the application.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md) | Obtains the total downlink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md) | Obtains the total downlink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md) | Obtains the total uplink traffic of all NICs (in bytes) from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md) | Obtains the total uplink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md) | Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md) | Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md) | Obtains the total uplink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md) | Obtains the total uplink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md) | Obtains the total downlink traffic of the specified NIC from the last startup to the time when this API is called (in bytes). This API uses an asynchronous callback to return the result. |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md) | Obtains the total downlink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md) | Obtains the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md) | Obtains the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getSelfTrafficStats](arkts-network-statistics-getselftrafficstats-f.md) | Obtains the traffic statistics of the specified application on the specified network within the specified period. This API uses a promise to return the result. |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md) | Obtains the downlink traffic (in bytes) of the specified socket. This API uses an asynchronous callback to return the result. |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md) | Obtains the downlink traffic (in bytes) of the specified socket. This API uses a promise to return the result. |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md) | Obtains the uplink traffic of the specified socket (in bytes). This API uses an asynchronous callback to return the result. |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md) | Obtains the uplink traffic (in bytes) of the specified socket. This API uses a promise to return the result. |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md) | Obtains the total downlink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md) | Obtains the total downlink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md) | Obtains the total uplink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md) | Obtains the total uplink traffic of the specified application from the last startup to the time when this API is called (in bytes). This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getMonthTrafficStats](arkts-network-statistics-getmonthtrafficstats-f-sys.md) | Get this month traffic data of the cellular network. |
| [getTrafficPlanInfo](arkts-network-statistics-gettrafficplaninfo-f-sys.md) | Get traffic plan info. |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md) | Obtains the historical data traffic of the specified NIC. This API uses an asynchronous callback to return the result. |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md) | Obtains the historical data traffic of the specified NIC. This API uses a promise to return the result. |
| [getTrafficStatsByNetwork](arkts-network-statistics-gettrafficstatsbynetwork-f-sys.md) | Obtains the traffic statistics of all applications on the specified network within the specified period. This API uses a promise to return the result. |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md) | Obtains the historical data traffic of the specified application. This API uses an asynchronous callback to return the result. |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md) | Obtains the historical data traffic of the specified application. This API uses a promise to return the result. |
| [getTrafficStatsByUidNetwork](arkts-network-statistics-gettrafficstatsbyuidnetwork-f-sys.md) | Obtains the traffic statistics of the specified application on the specified network within the specified period. This method uses a promise to return the result. |
| [off](arkts-network-statistics-off-f-sys.md#offnetstatschange) | Unsubscribes from traffic change events. This API uses an asynchronous callback to return the result. |
| [on](arkts-network-statistics-on-f-sys.md#onnetstatschange) | Subscribes to traffic change events. This API uses an asynchronous callback to return the result. |
| [setCalibrationTraffic](arkts-network-statistics-setcalibrationtraffic-f-sys.md) | Sets traffic calibration data. You can use this API to set traffic data during traffic calibration. This API uses a promise to return the result. |
| [setTrafficPlanInfo](arkts-network-statistics-settrafficplaninfo-f-sys.md) | Set traffic plan info. |
| [updateIfacesStats](arkts-network-statistics-updateifacesstats-f-sys.md) | Updates network interface statistics data. |
| [updateStatsData](arkts-network-statistics-updatestatsdata-f-sys.md) | Updates network statistics data. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md) | Defines the historical traffic information. |
| [NetworkInfo](arkts-network-statistics-networkinfo-i.md) | Defines the network information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md) | Defines the parameters for querying historical traffic of an NIC. |
| [NetStatsChangeInfo](arkts-network-statistics-netstatschangeinfo-i-sys.md) | Defines the NIC status and usage of an application. |
| [UidInfo](arkts-network-statistics-uidinfo-i-sys.md) | Defines the parameters for querying historical traffic of an application. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | Defines the fields related to the traffic plan. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [NetBearType](arkts-network-statistics-netbeartype-t.md) | Defines the network type. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [UidNetStatsInfo](arkts-network-statistics-uidnetstatsinfo-t-sys.md) |  |
<!--DelEnd-->
