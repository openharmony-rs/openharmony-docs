# getCellularRxBytes

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getCellularRxBytes

```TypeScript
function getCellularRxBytes(callback: AsyncCallback<number>): void
```

Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> It is recommended to call this API when the cellular network is in the connected state. Otherwise, error code 210
> 3012 will be thrown.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the traffic data is successfully obtained, **error** is **undefined**; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2103005](../errorcode-net-statistics.md#2103005-failed-to-read-the-system-map) | Failed to read the system map. |
| [2103011](../errorcode-net-statistics.md#2103011-failed-to-create-a-system-map) | Failed to create a system map. |
| [2103012](../errorcode-net-statistics.md#2103012-failed-to-obtain-the-nic-name) | Failed to obtain the NIC name. |

**Examples**

```TypeScript
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


<a id="getcellularrxbytes-1"></a>

## getCellularRxBytes

```TypeScript
function getCellularRxBytes(): Promise<number>
```

Obtains the total downlink traffic (in bytes) of the NIC corresponding to the currently connected cellular network from the last startup to the time when this API is called. This API uses a promise to return the result.

> **NOTE:** 
> 
> It is recommended to call this API when the cellular network is in the connected state. Otherwise, error code 210
> 3012 will be thrown.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the total downlink traffic (in bytes) of the specified NIC from the last startup to the time when the API is called. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2103005](../errorcode-net-statistics.md#2103005-failed-to-read-the-system-map) | Failed to read the system map. |
| [2103011](../errorcode-net-statistics.md#2103011-failed-to-create-a-system-map) | Failed to create a system map. |
| [2103012](../errorcode-net-statistics.md#2103012-failed-to-obtain-the-nic-name) | Failed to obtain the NIC name. |

**Examples**

```TypeScript
import { statistics } from '@kit.NetworkKit';

statistics.getCellularRxBytes().then((stats: number) => {
  console.info('getCellularRxBytes success', JSON.stringify(stats));
}).catch((error: Error) => {
   console.error('getCellularRxBytes error', JSON.stringify(error));
});
```
