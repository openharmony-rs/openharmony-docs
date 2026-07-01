# @ohos.net.statistics (Traffic Management)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:52:47.455Z pushedAt=2026-06-26T03:00:41.308Z -->

The Traffic Management module provides the capability to obtain device network traffic data. This module supports querying packet traffic usage from multiple dimensions, for example:

- Obtaining the uplink/downlink traffic data of a specified NIC.

- Obtaining the total traffic data of all NICs, facilitating the viewing of overall device network usage.

- Obtaining the traffic data of a specified application based on the application UID, helping you monitor the network resource consumption of applications.

- Obtaining traffic statistics for a specified socket, providing a data foundation for fine-grained network performance analysis.

- Obtaining the historical traffic usage of an application within a specified time period, facilitating the analysis of long-term network usage trends of the application.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { statistics } from '@kit.NetworkKit';
```

## statistics.getIfaceRxBytes

getIfaceRxBytes(nic: string, callback: AsyncCallback\<number>): void

Obtains the total downlink traffic of the specified NIC from the last startup to the time when this API is called (in bytes). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                   |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| nic      | string                 | Yes  | NIC name.                                                                                                     |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

statistics.getIfaceRxBytes("wlan0", (error: BusinessError, stats: number) => {
  if (error) {
    console.error(`getIfaceRxBytes error, ${JSON.stringify(error)}`);
    return;
  }
  console.info(`getIfaceRxBytes success, ${JSON.stringify(stats)}`);
});
```

## statistics.getIfaceRxBytes

getIfaceRxBytes(nic: string): Promise\<number>

Obtains the total downlink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| nic    | string | Yes  | NIC name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total downlink traffic (in bytes) of the specified NIC from the last startup to the current moment. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

statistics.getIfaceRxBytes("wlan0").then((stats: number) => {
  console.info(JSON.stringify(stats));
}).catch((err: BusinessError) => {
  console.error(JSON.stringify(err));
});
```

## statistics.getIfaceTxBytes

getIfaceTxBytes(nic: string, callback: AsyncCallback\<number>): void

Obtains the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                   |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| nic      | string                 | Yes  | NIC name.                                                                                                     |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

statistics.getIfaceTxBytes("wlan0", (error: BusinessError, stats: number) => {
  if (error) {
    console.error(`getIfaceTxBytes error, ${JSON.stringify(error)}`);
    return;
  }
  console.info(`getIfaceTxBytes success, ${JSON.stringify(stats)}`);
});
```

## statistics.getIfaceTxBytes

getIfaceTxBytes(nic: string): Promise\<number>

Obtains the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when this API is called. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| nic    | string | Yes  | NIC name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total uplink traffic (in bytes) of the specified NIC from the last startup to the time when the API is called. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

statistics.getIfaceTxBytes("wlan0").then((stats: number) => {
  console.info(`getIfaceTxBytes success, ${JSON.stringify(stats)}`);
}).catch((err: BusinessError) => {
   console.error(`getIfaceTxBytes error, ${JSON.stringify(err)}`);
});
```

## statistics.getCellularRxBytes

getCellularRxBytes(callback: AsyncCallback\<number>): void

Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> It is recommended to call this API when the cellular network is in the connected state. Otherwise, error code 2103012 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                   |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

statistics.getCellularRxBytes((error: BusinessError, stats: number) => {
  if (error) {
    console.error(`getCellularRxBytes error, ${JSON.stringify(error)}`);
    return;
  }
  console.info(`getCellularRxBytes success, ${JSON.stringify(stats)}`);
});
```

## statistics.getCellularRxBytes

getCellularRxBytes(): Promise\<number>

Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result.

> **NOTE**
>
> It is recommended to call this API when the cellular network is in the connected state. Otherwise, error code 2103012 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total downlink traffic (in bytes) of the specified NIC from the last startup to the time when the API is called. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

statistics.getCellularRxBytes().then((stats: number) => {
  console.info('getCellularRxBytes success', JSON.stringify(stats));
}).catch((error: Error) => {
   console.error('getCellularRxBytes error', JSON.stringify(error));
});
```

## statistics.getCellularTxBytes

getCellularTxBytes(callback: AsyncCallback\<number>): void

Obtains the total uplink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> It is recommended to call this API when the cellular network is in the connected state. Otherwise, error code 2103012 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                   |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

statistics.getCellularTxBytes((error: BusinessError, stats: number) => {
   if (error) {
    console.error(`getCellularTxBytes error, ${JSON.stringify(error)}`);
    return;
  }
  console.info(`getCellularTxBytes success, ${JSON.stringify(stats)}`);
});
```

## statistics.getCellularTxBytes

getCellularTxBytes(): Promise\<number>

Obtains the total uplink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result.

> **NOTE**
>
> It is recommended to call this API when the cellular network is in the connected state. Otherwise, error code 2103012 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total uplink traffic (in bytes) consumed on the cellular network since the last startup to the current moment. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |
| 2103012   | Failed to obtain the NIC name.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

statistics.getCellularTxBytes().then((stats: number) => {
  console.info('getCellularTxBytes success', JSON.stringify(stats));
}).catch((error: Error) => {
   console.error('getCellularTxBytes error', JSON.stringify(error));
});
```

## statistics.getAllRxBytes

getAllRxBytes(callback: AsyncCallback\<number>): void

Obtains the total downlink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                         |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service. |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

statistics.getAllRxBytes((error: BusinessError, stats: number) => {
  if (error) {
    console.error(JSON.stringify(error));
    return;
  }
  console.info(JSON.stringify(stats));
});
```

## statistics.getAllRxBytes

getAllRxBytes(): Promise\<number>

Obtains the total downlink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total downlink traffic (in bytes) of all NICs from the last startup to the current moment. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

statistics.getAllRxBytes().then((stats: number) => {
  console.info('getAllRxBytes success', JSON.stringify(stats));
}).catch((error: Error) => {
   console.error('getAllRxBytes error', JSON.stringify(error));
});
```

## statistics.getAllTxBytes

getAllTxBytes(callback: AsyncCallback\<number>): void

Obtains the total uplink traffic of all NICs (in bytes) from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                         |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

statistics.getAllTxBytes((error: BusinessError, stats: number) => {
  if (error) {
    console.error(JSON.stringify(error));
    return;
  }
  console.info(JSON.stringify(stats));
});
```

## statistics.getAllTxBytes

getAllTxBytes(): Promise\<number>

Obtains the total uplink traffic (in bytes) of all NICs from the last startup to the time when this API is called. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the real-time uplink traffic (in bytes) of all NICs. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

statistics.getAllTxBytes().then((stats: number) => {
  console.info(JSON.stringify(stats));
});
```

## statistics.getUidRxBytes

getUidRxBytes(uid: number, callback: AsyncCallback\<number>): void

Obtains the total downlink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> If the application has not generated any traffic consumption after the restart, error code 2103005 will be thrown.<br>

**Required permissions**

- API versions earlier than API version 26.0.0: N/A

- Since API version 26.0.0: **ohos.permission.GET_NETWORK_STATS** (You need to apply for this permission only when the value of **uid** is different from that of the API caller, that is, when you query the traffic data of other applications.)

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                   |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| uid      | number                 | Yes  | Application UID.                                                                                                   |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let uid = 123456789;  // This is a sample UID. Replace it with the actual UID.
statistics.getUidRxBytes(uid, (error: BusinessError, stats: number) => {
  if (error) {
     console.error(JSON.stringify(error));
     return;
  }
  console.info(JSON.stringify(stats));
});
```

## statistics.getUidRxBytes

getUidRxBytes(uid: number): Promise\<number>

Obtains the total downlink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses a promise to return the result.

> **NOTE**
>
> If the application has not generated any traffic consumption after the restart, error code 2103005 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permissions**

- API versions earlier than API version 26.0.0: N/A

- Since API version 26.0.0: **ohos.permission.GET_NETWORK_STATS** (You need to apply for this permission only when the value of **uid** is different from that of the API caller, that is, when you query the traffic data of other applications.)

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| uid    | number | Yes  | Application UID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total downlink traffic (in bytes) of the specified application from the last startup to the current moment. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

let uid = 123456789;  // This is a sample UID. Replace it with the actual UID.
statistics.getUidRxBytes(uid).then((stats: number) => {
  console.info(JSON.stringify(stats));
});
```

## statistics.getUidTxBytes

getUidTxBytes(uid: number, callback: AsyncCallback\<number>): void

Obtains the total uplink traffic (in bytes) of the specified application from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> If the application has not generated any traffic consumption after the restart, error code 2103005 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permissions**

- API versions earlier than API version 26.0.0: N/A

- Since API version 26.0.0: **ohos.permission.GET_NETWORK_STATS** (You need to apply for this permission only when the value of **uid** is different from that of the API caller, that is, when you query the traffic data of other applications.)

**Parameters**

| Name  | Type                  | Mandatory| Description                                                                                                                   |
| -------- | ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| uid      | number                 | Yes  | Application UID.                                                                                                   |
| callback | AsyncCallback\<number> | Yes | Callback used to return the result. If the application's real-time uplink traffic is successfully obtained, **error** is **undefined** and **stats** is the obtained application uplink traffic (in bytes). Otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let uid = 123456789;  // This is a sample UID. Replace it with the actual UID.
statistics.getUidTxBytes(uid, (error: BusinessError, stats: number) => {
  if (error) {
    console.error(JSON.stringify(error));
    return;
  }
  console.info(JSON.stringify(stats));
});
```

## statistics.getUidTxBytes

getUidTxBytes(uid: number): Promise\<number>

Obtains the total uplink traffic of the specified application from the last startup to the time when this API is called (in bytes). This API uses a promise to return the result.

> **NOTE**
>
> If the application has not generated any traffic consumption after the restart, error code 2103005 will be thrown.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permissions**

- API versions earlier than API version 26.0.0: N/A

- Since API version 26.0.0: **ohos.permission.GET_NETWORK_STATS** (You need to apply for this permission only when the value of **uid** is different from that of the API caller, that is, when you query the traffic data of other applications.)

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| uid    | number | Yes  | Application UID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the total uplink traffic (in bytes) of the specified application from the last startup to the time when the API is called. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103005   | Failed to read the system map.               |
| 2103011   | Failed to create a system map.               |

**Example**

```js
import { statistics } from '@kit.NetworkKit';

let uid = 123456789;  // This is a sample UID. Replace it with the actual UID.
statistics.getUidTxBytes(uid).then((stats: number) => {
  console.info(JSON.stringify(stats));
});
```

## statistics.getSockfdRxBytes<sup>11+</sup>

getSockfdRxBytes(sockfd: number, callback: AsyncCallback\<number\>): void

Obtains the downlink traffic (in bytes) of the specified socket. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> It is recommended to use this API when the socket is connected. Otherwise, the corresponding traffic data cannot be queried after the socket is closed.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| sockfd   | number                 | Yes  | File description (FD) of the socket to query.                     |
| callback | AsyncCallback\<number> | Yes  | Callback used to return the result. If the downlink traffic of the socket is obtained successfully, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // In actual development, you need to first obtain it based on the socket you created.
statistics.getSockfdRxBytes(sockfd, (error: BusinessError, stats: number) => {
  if (error) {
    console.error(JSON.stringify(error));
    return;
  }
  console.info(JSON.stringify(stats));
});
```

## statistics.getSockfdRxBytes<sup>11+</sup>

getSockfdRxBytes(sockfd: number): Promise\<number\>

Obtains the downlink traffic (in bytes) of the specified socket. This API uses a promise to return the result.

> **NOTE**
>
> It is recommended to use this API when the socket is connected. Otherwise, the corresponding traffic data cannot be queried after the socket is closed.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | ---------------------------------------- |
| sockfd | number | Yes | FD of the socket to query. |

**Return value**

| Type            | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| Promise\<number> | Promise used to return the downlink traffic (in bytes) of the socket. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // In actual development, you need to first obtain it based on the socket you created.
statistics.getSockfdRxBytes(sockfd).then((stats: number) => {
  console.info(JSON.stringify(stats));
}).catch((err: BusinessError) => {
  console.error(JSON.stringify(err));
});
```

## statistics.getSockfdTxBytes<sup>11+</sup>

getSockfdTxBytes(sockfd: number, callback: AsyncCallback\<number\>): void

Obtains the uplink traffic of the specified socket (in bytes). This API uses an asynchronous callback to return the result.

> **NOTE**
>
> It is recommended to use this API when the socket is connected. Otherwise, the corresponding traffic data cannot be queried after the socket is closed.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| sockfd   | number                 | Yes  | FD of the socket to query.                     |
| callback | AsyncCallback\<number> | Yes  | Callback used to return the result. If the uplink traffic of the socket is obtained successfully, **error** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // In actual development, you need to first obtain it based on the socket you created.
statistics.getSockfdTxBytes(sockfd, (error: BusinessError, stats: number) => {
  if (error) {
    console.error(JSON.stringify(error));
    return;
  }
  console.info(JSON.stringify(stats));
});
```

## statistics.getSockfdTxBytes<sup>11+</sup>

getSockfdTxBytes(sockfd: number): Promise\<number\>

Obtains the uplink traffic (in bytes) of the specified socket. This API uses a promise to return the result.

> **NOTE**
>
> It is recommended to use this API when the socket is connected. Otherwise, the corresponding traffic data cannot be queried after the socket is closed.<br>

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | ---------------------------------------- |
| sockfd | number | Yes | FD of the socket to query. |

**Return value**

| Type            | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| Promise\<number> | Promise used to return the uplink traffic (in bytes) of the socket. |

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // In actual development, you need to first obtain it based on the socket you created.
statistics.getSockfdTxBytes(sockfd).then((stats: number) => {
  console.info(JSON.stringify(stats));
}).catch((err: BusinessError) => {
  console.error(JSON.stringify(err));
});
```

## statistics.getSelfTrafficStats<sup>22+</sup>

getSelfTrafficStats(networkInfo: NetworkInfo): Promise\<NetStatsInfo\>

Obtains the traffic statistics of the specified application on the specified network within the specified period. This API uses a promise to return the result.

> **NOTE**
>
>- Currently, only cellular and Wi-Fi traffic usage can be obtained.<br>
>- Currently, only traffic usage within the last 31 days can be obtained. If the timestamp passed in the parameter is earlier than 31 days before the current system time, error code 2103019 will be returned.
>- This API may take some time to execute. Do not call it frequently.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | ---------------------------------------- |
| networkInfo | [NetworkInfo](#networkinfo22) | Yes  | Network information.|

**Return value**

| Type            | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| Promise\<[NetStatsInfo](#netstatsinfo22)> | Promise used to return the historical traffic statistics of the application.|

**Error codes**

For details about the error codes, see [Traffic Management Error Codes](errorcode-net-statistics.md).

| ID| Error Message                                    |
| --------- | -------------------------------------------- |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |
| 2103017   | Failed to read the database.                      |
| 2103019   | The timestamp in param is invalid.                      |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { connection, statistics } from '@kit.NetworkKit';

let networkInfo: statistics.NetworkInfo = {
    type: connection.NetBearType.BEARER_CELLULAR,
    startTime: Math.floor(Date.now() / 1000) - 86400 * 31,
    endTime: Math.floor(Date.now() / 1000),
    simId: 1,
}

statistics.getSelfTrafficStats(networkInfo).then((stats: statistics.NetStatsInfo) => {
    console.info('getSelfTrafficStats success : ' + JSON.stringify(stats));
}).catch((err: BusinessError) => {
    console.error('getSelfTrafficStats error. code: ' + `${err.code}` + ', message: ' + `${err.message}`);
});
```

## NetBearType<sup>12+</sup>

type NetBearType = connection.NetBearType

Defines the network type.

**System capability**: SystemCapability.Communication.NetManager.Core

|       Type      |            Description            |
| ---------------- | --------------------------- |
| [connection.NetBearType](js-apis-net-connection.md#netbeartype) | Network type.   |

## NetworkInfo<sup>22+</sup>

Defines the network information.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name       | Type                                                  | Read-Only|Optional| Description          |
|-----------|------------------------------------------------------|----|---|--------------|
| type      | [NetBearType](#netbeartype12) | No | No|Network type.<br>**Note**: If **type** is set to **cellular**, the **simId** field must be specified.      |
| startTime | number                                               | No  | No | Start timestamp, in seconds. |
| endTime   | number                                               | No  | No | End timestamp, in seconds. |
| simId     | number                                               | No | Yes|SIM card ID. The default value is the maximum value of the uint32_t type.<br>**Note**: If **type** is set to **cellular**, this field must be specified.  |

## NetStatsInfo<sup>22+</sup>

Defines the historical traffic information.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name     | Type  | Read-Only|Optional| Description                     |
| --------- | ------ | ---- |---| ------------------------ |
| rxBytes   | number | No   |No |Downlink traffic data (unit: bytes). |
| txBytes   | number | No   |No |Uplink traffic data (unit: bytes). |
| rxPackets | number | No  |No|Number of downlink packets.         |
| txPackets | number | No  |No|Number of uplink packets.         |