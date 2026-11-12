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

<!--Device-unnamed-declare namespace statistics--><!--Device-unnamed-declare namespace statistics-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md#getallrxbytes-1) | Obtains the total downlink traffic of all network cards from the last boot to the time of interface call (in bytes). This API uses an asynchronous callback to return the result. |
| [getAllRxBytes](arkts-network-statistics-getallrxbytes-f.md#getallrxbytes-2) | Obtains the total downlink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md#getalltxbytes-1) | Obtains the total uplink traffic of all NICs (in bytes) from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getAllTxBytes](arkts-network-statistics-getalltxbytes-f.md#getalltxbytes-2) | Obtains the total uplink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md#getcellularrxbytes-1) | Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getCellularRxBytes](arkts-network-statistics-getcellularrxbytes-f.md#getcellularrxbytes-2) | Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md#getcellulartxbytes-1) | Obtains the total uplink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getCellularTxBytes](arkts-network-statistics-getcellulartxbytes-f.md#getcellulartxbytes-2) | Obtains the total uplink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md#getifacerxbytes-1) | Obtains the total downlink traffic of the specified NIC from the last startup to the time when this API is called (in bytes). This API uses an asynchronous callback to return the result. |
| [getIfaceRxBytes](arkts-network-statistics-getifacerxbytes-f.md#getifacerxbytes-2) | Obtains the total downlink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md#getifacetxbytes-1) | Obtains the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getIfaceTxBytes](arkts-network-statistics-getifacetxbytes-f.md#getifacetxbytes-2) | Obtains the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getSelfTrafficStats](arkts-network-statistics-getselftrafficstats-f.md#getselftrafficstats-1) | Obtains the traffic statistics of the specified application on the specified network within the specified period. This API uses a promise to return the result. |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md#getsockfdrxbytes-1) | Obtains the downlink traffic (in bytes) of the specified socket. This API uses an asynchronous callback to return the result. |
| [getSockfdRxBytes](arkts-network-statistics-getsockfdrxbytes-f.md#getsockfdrxbytes-2) | Obtains the downlink traffic (in bytes) of the specified socket. This API uses a promise to return the result. |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md#getsockfdtxbytes-1) | Obtains the uplink traffic of the specified socket (in bytes). This API uses an asynchronous callback to return the result. |
| [getSockfdTxBytes](arkts-network-statistics-getsockfdtxbytes-f.md#getsockfdtxbytes-2) | Obtains the uplink traffic (in bytes) of the specified socket. This API uses a promise to return the result. |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md#getuidrxbytes-1) | Obtains the total downlink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getUidRxBytes](arkts-network-statistics-getuidrxbytes-f.md#getuidrxbytes-2) | Obtains the total downlink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses a promise to return the result. |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md#getuidtxbytes-1) | Obtains the total uplink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result. |
| [getUidTxBytes](arkts-network-statistics-getuidtxbytes-f.md#getuidtxbytes-2) | Obtains the total uplink traffic of the specified application from the last startup to the time when this API is called (in bytes). This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getMonthTrafficStats](arkts-network-statistics-getmonthtrafficstats-f-sys.md#getmonthtrafficstats-1) | Get this month traffic data of the cellular network. |
| [getTrafficPlanInfo](arkts-network-statistics-gettrafficplaninfo-f-sys.md#gettrafficplaninfo-1) | Get traffic plan info. |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md#gettrafficstatsbyiface-1) | Obtains the historical traffic information of the specified network interface. This API uses an asynchronous callback to return the result. Based on the network interface name and time range specified in **ifaceInfo**, the system reads the transmitted and received bytes and packets of the network interface in the corresponding period from the statistics database and returns them through the callback. If the network interface name is invalid or no statistics are available in the period, all-zero statistics are returned. |
| [getTrafficStatsByIface](arkts-network-statistics-gettrafficstatsbyiface-f-sys.md#gettrafficstatsbyiface-2) | Obtains the historical traffic information of the specified network interface. This API uses a promise to return the result. Based on the network interface name and time range specified in **ifaceInfo**, the system reads the transmitted and received bytes and packets of the network interface in the corresponding period from the statistics database and returns them in a promise. If the network interface name is invalid or no statistics are available in the period, all-zero statistics are returned. |
| [getTrafficStatsByNetwork](arkts-network-statistics-gettrafficstatsbynetwork-f-sys.md#gettrafficstatsbynetwork-1) | Obtains the traffic usage details of all applications on the specified network within the specified period. This API uses a promise to return the result. Based on the network type, time range, and **simId** in **networkInfo**, the system aggregates the historical traffic data of each application (by UID) on the network from the statistics database and returns **UidNetStatsInfo** in a promise. The **simId** takes effect only when the network type is cellular (**BEARER_CELLULAR**). |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md#gettrafficstatsbyuid-1) | Obtains the historical traffic information of the specified application. This API uses an asynchronous callback to return the result. Based on the application UID, network interface, and time range specified in **uidInfo**, the system reads the transmitted and received bytes and packets of the application in the corresponding period from the statistics database and returns them through the callback. If the application has no traffic records in the specified period, all-zero statistics are returned. |
| [getTrafficStatsByUid](arkts-network-statistics-gettrafficstatsbyuid-f-sys.md#gettrafficstatsbyuid-2) | Obtains the historical traffic information of the specified application. This API uses a promise to return the result. Based on the application UID, network interface, and time range specified in **uidInfo**, the system reads the transmitted and received bytes and packet counts of the application within the corresponding period from the statistics database and returns them in a promise. If the application has no traffic records within the specified period, all-zero statistics are returned. |
| [getTrafficStatsByUidNetwork](arkts-network-statistics-gettrafficstatsbyuidnetwork-f-sys.md#gettrafficstatsbyuidnetwork-1) | Obtains the traffic usage details of the application on the specified network within the specified period. This API uses a promise to return the result. Based on the UID and the network type, time range, and **simId** in **networkInfo**, the system reads the historical traffic data of the application on the specified network from the statistics database, returns a **NetStatsInfoSequence** sequence by time period, and returns it in a promise. The **simId** takes effect only when the network type is cellular (**BEARER_CELLULAR**). |
| [off('netStatsChange')](arkts-network-statistics-off-f-sys.md#offnetstatschange) | Unsubscribes from traffic change events. This API uses an asynchronous callback to return the result. |
| [on('netStatsChange')](arkts-network-statistics-on-f-sys.md#onnetstatschange) | Subscribes to traffic change events. This API uses an asynchronous callback to return the result. |
| [setCalibrationTraffic](arkts-network-statistics-setcalibrationtraffic-f-sys.md#setcalibrationtraffic-1) | Sets traffic calibration data. During traffic calibration, you can use this API to set the related traffic data. The API writes the remaining traffic (**remainTraffic**) and the total traffic of the plan (**totalTraffic**) corresponding to **simId** into the system traffic statistics database for subsequent traffic statistics and calibration calculation. The calibration result takes effect on the data returned by subsequent query APIs. This API uses a promise to return the result. |
| [setTrafficPlanInfo](arkts-network-statistics-settrafficplaninfo-f-sys.md#settrafficplaninfo-1) | Set traffic plan info. |
| [updateIfacesStats](arkts-network-statistics-updateifacesstats-f-sys.md#updateifacesstats-1) | Updates network interface statistics data. |
| [updateStatsData](arkts-network-statistics-updatestatsdata-f-sys.md#updatestatsdata-1) | Updates network statistics data. |
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
| [NetStatsChangeInfo](arkts-network-statistics-netstatschangeinfo-i-sys.md) | NIC name and application UID reported in a traffic change event. |
| [UidInfo](arkts-network-statistics-uidinfo-i-sys.md) | Defines the parameters for querying historical traffic of an application. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [NetBearType](arkts-network-statistics-netbeartype-t.md) | Defines the network type. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [UidNetStatsInfo](arkts-network-statistics-uidnetstatsinfo-t-sys.md) | Defines the historical traffic statistics of all applications. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [TrafficPlanParam](arkts-network-statistics-trafficplanparam-e-sys.md) | Defines the fields related to the traffic plan. |
<!--DelEnd-->
