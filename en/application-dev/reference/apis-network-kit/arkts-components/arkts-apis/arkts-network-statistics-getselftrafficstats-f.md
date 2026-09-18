# getSelfTrafficStats

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getSelfTrafficStats

```TypeScript
function getSelfTrafficStats(networkInfo: NetworkInfo): Promise<NetStatsInfo>
```

Obtains the traffic statistics of the specified application on the specified network within the specified period. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Currently, only cellular and Wi-Fi traffic usage can be obtained.

> - Currently, only traffic usage within the last 31 days can be obtained. If the timestamp passed in the parameter is earlier than 31 days before the current system time, error code 2103019 will be returned.
> 
> - This API may take some time to execute. Do not call it frequently.

**Since:** 22

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkInfo | [NetworkInfo](arkts-network-statistics-networkinfo-i.md) | Yes | Network information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md)&gt; | Promise used to return the historical traffic statistics of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2103017](../errorcode-net-statistics.md#2103017-failed-to-read-the-database) | Failed to read the database. |
| [2103019](../errorcode-net-statistics.md#2103019-invalid-timestamp) | The timestamp in param is invalid. |

**Examples**

```TypeScript
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
