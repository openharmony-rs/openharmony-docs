# @ohos.net.statistics (Traffic Management) (System API)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ffd0c41b3527cce8153c2d24375b64d72b05d20b translatedAt=2026-11-04T02:44:31.832Z pushedAt=2026-11-04T03:24:28.613Z nl=1 -->

The **statistics** module provides APIs to query real-time or historical traffic statistics by the specified network interface card (NIC) or user ID (UID).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.net.statistics (Traffic Management)](js-apis-net-statistics.md).

## Modules to Import

```js
import { statistics } from '@kit.NetworkKit';
```


## statistics.on('netStatsChange')

on(type: 'netStatsChange', callback: Callback\<NetStatsChangeInfo\>): void

Subscribes to traffic change events. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                              |
| -------- | ------------------------------------------- | ---- | ----------------------------------------------------------------- |
| type     | string                                      | Yes  | Event type. This field has a fixed value of **netStatsChange**.                                |
| callback | Callback\<[NetStatsChangeInfo](#netstatschangeinfo11)\> | Yes  | Callback invoked when the traffic changes.|

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

class IFace {
  iface: string = ""
  uid?: number = 0
}
statistics.on('netStatsChange', (data: IFace) => {
  console.error('on netStatsChange' + JSON.stringify(data));
});
```

## statistics.off('netStatsChange')

off(type: 'netStatsChange', callback?: Callback\<NetStatsChangeInfo>): void

Unsubscribes from traffic change events. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                              |
| -------- | ------------------------------------------- | ---- | ----------------------------------------------------------------- |
| type     | string                                      | Yes   | Unsubscribe event, fixed to 'netStatsChange'.                             |
| callback | Callback\<[NetStatsChangeInfo](#netstatschangeinfo11)\> | No   | Callback for the netStatsChange event, which is registered through on('netStatsChange'). |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

class IFace {
  iface: string = ""
  uid?: number = 0
}
let callback: (data: IFace) => void = (data: IFace) => {
    console.info("on netStatsChange, iFace:" + data.iface + " uid: " + data.uid);
}
statistics.on('netStatsChange', callback);
// You can pass the callback of the on method to cancel listening for a certain type of callback. If you do not pass the callback, you will cancel listening for all callbacks.
statistics.off('netStatsChange', callback);
statistics.off('netStatsChange');
```

## statistics.getTrafficStatsByIface

getTrafficStatsByIface(ifaceInfo: IfaceInfo, callback: AsyncCallback\<NetStatsInfo>): void

Obtains the historical traffic information of a specified network card. This API uses an asynchronous callback to return the result. Based on the network card name and time range specified in ifaceInfo, the system reads the sent and received bytes and packets of the network card within the corresponding time period from the traffic statistics database and returns them through the callback. If the network card name is invalid or no statistics data exists within the time period, all-zero statistics information is returned.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                           | Mandatory| Description                                                                                   |
| --------- | ----------------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
| ifaceInfo | [IfaceInfo](#ifaceinfo)                       | Yes  | NIC information. For details, see [IfaceInfo](#ifaceinfo).                                    |
| callback  | AsyncCallback\<[NetStatsInfo](js-apis-net-statistics.md#netstatsinfo22)> | Yes   | Callback invoked to return the network card historical traffic information. On success, statsInfo returns the network card historical traffic information and error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                 |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let iFaceInfo: statistics.IfaceInfo | null = null;
if (iFaceInfo) {
  statistics.getTrafficStatsByIface(iFaceInfo as statistics.IfaceInfo, (error: BusinessError, statsInfo: statistics.NetStatsInfo) => {
    if (error) {
      console.error(JSON.stringify(error));
      return;
    };
    console.info(
      "getTrafficStatsByIface bytes of received = " +
      JSON.stringify(statsInfo.rxBytes)
    );
    console.info(
      "getTrafficStatsByIface bytes of sent = " +
      JSON.stringify(statsInfo.txBytes)
    );
    console.info(
      "getTrafficStatsByIface packets of received = " +
      JSON.stringify(statsInfo.rxPackets)
    );
    console.info(
      "getTrafficStatsByIface packets of sent = " +
      JSON.stringify(statsInfo.txPackets)
    );
  });
}
```

## statistics.getTrafficStatsByIface

getTrafficStatsByIface(ifaceInfo: IfaceInfo): Promise\<NetStatsInfo>

Obtains the historical traffic information of a specified network card. This API uses a promise to return the result. Based on the network card name and time range specified in ifaceInfo, the system reads the sent and received bytes and packets of the network card within the corresponding time period from the traffic statistics database and returns them in a promise. If the network card name is invalid or no statistics data exists within the time period, all-zero statistics information is returned.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

| Name   | Type                     | Mandatory| Description                                               |
| --------- | ------------------------- | ---- | --------------------------------------------------- |
| ifaceInfo | [IfaceInfo](#ifaceinfo) | Yes  | NIC information. For details, see [IfaceInfo](#ifaceinfo).|

**Return value**
| Type| Description|
| -------- | -------- |
| Promise\<[NetStatsInfo](js-apis-net-statistics.md#netstatsinfo22)> | Returns the result in Promise form, which is the network card historical traffic information. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                 |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

let iFaceInfo: statistics.IfaceInfo | null = null;
if (iFaceInfo) {
  statistics.getTrafficStatsByIface(iFaceInfo as statistics.IfaceInfo).then((statsInfo: statistics.NetStatsInfo) => {
    console.info(
      "getTrafficStatsByIface bytes of received = " +
      JSON.stringify(statsInfo.rxBytes)
    );
    console.info(
      "getTrafficStatsByIface bytes of sent = " +
      JSON.stringify(statsInfo.txBytes)
    );
    console.info(
      "getTrafficStatsByIface packets of received = " +
      JSON.stringify(statsInfo.rxPackets)
    );
    console.info(
      "getTrafficStatsByIface packets of sent = " +
      JSON.stringify(statsInfo.txPackets)
    );
  });
}
```

## statistics.getTrafficStatsByUid

getTrafficStatsByUid(uidInfo: UidInfo, callback: AsyncCallback\<NetStatsInfo>): void

Obtains the historical traffic information of a specified application. This API uses an asynchronous callback to return the result. Based on the application UID, network card, and time range specified in uidInfo, the system reads the sent and received bytes and packets of the application within the corresponding time period from the traffic statistics database and returns them through the callback. If the application has no traffic records within the specified time period, all-zero statistics information is returned.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                           | Mandatory| Description                                                                                   |
| -------- | ----------------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
| uidInfo  | [UidInfo](#uidinfo)                           | Yes  | Application information. For details, see [UidInfo](#uidinfo).                                        |
| callback | AsyncCallback\<[NetStatsInfo](js-apis-net-statistics.md#netstatsinfo22)> | Yes | Callback. On success, statsInfo returns the application historical traffic information and error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                 |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let uidInfo: statistics.UidInfo = {
  uid: 20010037,
  ifaceInfo: {
    iface: '',
    startTime: 1,
    endTime: 3,
  }
}

statistics.getTrafficStatsByUid(
  uidInfo,
  (error: BusinessError, statsInfo: statistics.NetStatsInfo) => {
    if (error) {
      console.error(JSON.stringify(error));
      return;
    };
    console.info(
      "getTrafficStatsByUid bytes of received = " +
      JSON.stringify(statsInfo.rxBytes)
    );
    console.info(
      "getTrafficStatsByUid bytes of sent = " +
      JSON.stringify(statsInfo.txBytes)
    );
    console.info(
      "getTrafficStatsByUid packets of received = " +
      JSON.stringify(statsInfo.rxPackets)
    );
    console.info(
      "getTrafficStatsByUid packets of sent = " +
      JSON.stringify(statsInfo.txPackets)
    );
  }
);
```

## statistics.getTrafficStatsByUid

getTrafficStatsByUid(uidInfo: UidInfo): Promise\<NetStatsInfo>

Obtains the historical traffic information of a specified application. This API uses a promise to return the result. Based on the application UID, network card, and time range specified in uidInfo, the system reads the sent and received bytes and packets of the application within the corresponding time period from the traffic statistics database and returns them in a promise. If the application has no traffic records within the specified time period, all-zero statistics information is returned.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name | Type                 | Mandatory| Description                                           |
| ------- | --------------------- | ---- | ----------------------------------------------- |
| uidInfo | [UidInfo](#uidinfo) | Yes  | Application information. For details, see [UidInfo](#uidinfo).|

**Return value**

| Type                                     | Description                                              |
| ----------------------------------------- | -------------------------------------------------- |
| Promise\<[NetStatsInfo](js-apis-net-statistics.md#netstatsinfo22)> | Returns the result in promise mode, returning the application historical traffic information. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                 |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

let uidInfo: statistics.UidInfo = {
  uid: 20010037,
  ifaceInfo: {
    iface: '',
    startTime: 1,
    endTime: 3,
  }
}

statistics.getTrafficStatsByUid(uidInfo).then((statsInfo: statistics.NetStatsInfo) => {
  console.info("getTrafficStatsByUid bytes of received = " + JSON.stringify(statsInfo.rxBytes));
  console.info("getTrafficStatsByUid bytes of sent = " + JSON.stringify(statsInfo.txBytes));
  console.info("getTrafficStatsByUid packets of received = " + JSON.stringify(statsInfo.rxPackets));
  console.info("getTrafficStatsByUid packets of sent = " + JSON.stringify(statsInfo.txPackets));
})
```

## statistics.getTrafficStatsByNetwork<sup>12+</sup>

getTrafficStatsByNetwork(networkInfo: NetworkInfo): Promise\<UidNetStatsInfo>

Obtains the traffic usage details of all applications on a specified network within a specified time period. This API uses a promise to return the result. Based on the network type, time range, and simId in networkInfo, the system aggregates the historical traffic data of each application (by UID) on the network from the traffic statistics database and returns UidNetStatsInfo in a promise. The simId takes effect only when the network type is cellular (BEARER_CELLULAR).

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name        | Type                           | Mandatory| Description                                        |
|-------------|-------------------------------|----|--------------------------------------------|
| networkInfo | [NetworkInfo](#networkinfo12) | Yes | Network information. For details, see [NetworkInfo](#networkinfo12).|

**Return value**

| Type                                             | Description                              |
|-------------------------------------------------|----------------------------------|
| Promise\<[UidNetStatsInfo](#uidnetstatsinfo12)> | Returns the result in Promise form. Returns the historical traffic information of all applications. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                 |

**Example**

```js
import { connection, statistics } from '@kit.NetworkKit';

let networkInfo: statistics.NetworkInfo = {
  type: connection.NetBearType.BEARER_CELLULAR,
  startTime: Math.floor(Date.now() / 1000) - 86400 * 7, 
  endTime: Math.floor(Date.now() / 1000) + 5,
  simId: 1,
}

statistics.getTrafficStatsByNetwork(networkInfo).then((statsInfo: statistics.UidNetStatsInfo) => {
  let rank: Map<string, object> = new Map<string, object>(Object.entries(statsInfo));
  rank.forEach((value: object, key: string) => {
    console.info("getTrafficStatsByNetwork key=" + key + ", value=" + JSON.stringify(value));
  })
})
```

## statistics.getTrafficStatsByUidNetwork<sup>12+</sup>

getTrafficStatsByUidNetwork(uid: number, networkInfo: NetworkInfo): Promise\<NetStatsInfoSequence>

Obtains the traffic usage details of an application on a specified network within a specified time period. This API uses a promise to return the result. Based on the UID and the network type, time range, and simId in networkInfo, the system reads the historical traffic data of the application on the specified network from the traffic statistics database, returns a NetStatsInfoSequence sequence by time period, and returns it in a promise. The simId takes effect only when the network type is cellular (BEARER_CELLULAR).

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name        | Type                           | Mandatory| Description                                        |
|-------------|-------------------------------|----|--------------------------------------------|
| uid         | number                        | Yes | Application UID.                              |
| networkInfo | [NetworkInfo](#networkinfo12) | Yes | Network information. For details, see [NetworkInfo](#networkinfo12).|

**Return value**

| Type                                                       | Description                              |
|-----------------------------------------------------------|----------------------------------|
| Promise\<[NetStatsInfoSequence](#netstatsinfosequence12)> | Returns the result in Promise form. Returns the application historical traffic statistics. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                 |

**Example**

```js
import { connection, statistics } from '@kit.NetworkKit';

let uid: number = 20020147;
let networkInfo: statistics.NetworkInfo = {
  type: connection.NetBearType.BEARER_CELLULAR,
  startTime: Math.floor(Date.now() / 1000) - 86400 * 7, 
  endTime: Math.floor(Date.now() / 1000) + 5,
  simId: 1,
}

statistics.getTrafficStatsByUidNetwork(uid, networkInfo).then((statsInfoSequence: statistics.NetStatsInfoSequence) => {
  for (let i = 0; i < statsInfoSequence.length; i++) {
    console.info("getTrafficStatsByUidNetwork item:" + JSON.stringify(statsInfoSequence[i]));
  }
})
```

## statistics.setCalibrationTraffic

setCalibrationTraffic(simId: number, remainTraffic: number, totalTraffic?: number): Promise\<void>;

Sets traffic calibration data. When calibrating traffic, you can use this API to set the related traffic data. The API writes the remaining traffic (remainTraffic) and the total traffic of the plan (totalTraffic) corresponding to simId into the system traffic statistics database for subsequent traffic statistics and calibration calculation. The calibration result takes effect on the data returned by subsequent query APIs. This API uses a promise to return the result.

**Since**: 26.0.0

**System API**: This is a system API.

**Model restriction:** This interface can be used only in the stage model.

**Required permissions**: ohos.permission.GET_NETWORK_STATS

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name        | Type                           | Mandatory| Description                                        |
|-------------|-------------------------------|----|--------------------------------------------|
| simId         | number                        | Yes | SIM card ID.                              |
| remainTraffic | number | Yes | Remaining traffic, in bytes.|
| totalTraffic | number | No | Total traffic, in bytes.|

**Return value**

| Type                                                       | Description                              |
|-----------------------------------------------------------|----------------------------------|
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 801       | Capability not supported.                             |
| 2100001   | Invalid parameter value, such as simId error.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error, such as nullptr.                       |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let simId:number = 1;
let remainData:number = 600*1024*1024;   // The remaining traffic is 600 MB.
let totalData:number = 1024*1024*1024;   // The total traffic is 1 GB.
statistics.setCalibrationTraffic(simId, remainData, totalData).then(() => {
  console.info(`setCalibrationTraffic succ`);
}).catch((error: BusinessError) => {
  console.info(`setCalibrationTraffic error. code:${error.code}, message:${error.message}`);
});
```

## IfaceInfo

Defines the parameters for querying historical traffic of an NIC.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name     | Type  | Read-Only|Optional|Description                             |
| --------- | ------ | ---- |---| --------------------------------- |
| iface     | string | No  |No|NIC name.                   |
| startTime | number | No  |No|Start time of the query, which is a timestamp in seconds.|
| endTime   | number | No | No|End time of the query, which is a timestamp in seconds.|

## UidInfo

Defines the parameters for querying historical traffic of an application.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name     | Type                                 | Read-Only|Optional| Description                       |
| --------- | ------------------------------------- | ---- |---| -------------------------- |
| ifaceInfo | [IfaceInfo](#ifaceinfo) | No | No | Network card and time parameter information to be queried. |
| uid       | number                                | No  |No|Application UID.         |

## NetStatsChangeInfo<sup>11+</sup>

Defines the network card name and application UID reported in a traffic change event.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name     | Type  | Read-Only|Optional| Description      |
| --------- | ------ | ---- |---|--------- |
| iface     | string | No  |No| NIC name.|
| uid       | number | No  |Yes|Application UID. |

## NetworkInfo<sup>12+</sup>

Defines the network information.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name       | Type                                                  | Read-Only|Optional| Description          |
|-----------|------------------------------------------------------|----|---|--------------|
| type      | [NetBearType](js-apis-net-connection.md#netbeartype) | No | No|Network type.       |
| startTime | number                                               | No |No| Start timestamp, in seconds.|
| endTime   | number                                               | No |No|End timestamp, in seconds.|
| simId     | number                                               | No | Yes|SIM card ID.   |

## UidNetStatsInfo<sup>12+</sup>

Defines the historical traffic statistics of all applications.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name       | Type                                           | Read-Only|Optional| Description          |
|-----------|-----------------------------------------------|----|---|--------------|
| [uid: number] | [NetStatsInfo](js-apis-net-statistics.md#netstatsinfo22) | No | No | Historical traffic information of all applications. |

## NetStatsInfoSequence<sup>12+</sup>

Defines the historical traffic statistics of the specified application.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name       | Type                             | Read-Only| Optional|Description          |
|-----------|---------------------------------|----|---|--------------|
| startTime | number                          | No |No|Start timestamp, in seconds.|
| endTime   | number                          | No |No|End timestamp, in seconds.|
| info      | [NetStatsInfo](js-apis-net-statistics.md#netstatsinfo22) | No  | No | Application historical traffic information obtained. |