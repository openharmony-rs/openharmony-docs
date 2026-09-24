# getSockfdTxBytes

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getSockfdTxBytes

```TypeScript
function getSockfdTxBytes(sockfd: number, callback: AsyncCallback<number>): void
```

Obtains the uplink traffic of the specified socket (in bytes). This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> It is recommended to use this API when the socket is connected. Otherwise, the corresponding traffic data cannot
> be queried after the socket is closed.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sockfd | number | Yes | FD of the socket to query. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the uplink traffic of the socket is obtained successfully, **error** is **undefined**; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
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


<a id="getsockfdtxbytes-1"></a>

## getSockfdTxBytes

```TypeScript
function getSockfdTxBytes(sockfd: number): Promise<number>
```

Obtains the uplink traffic (in bytes) of the specified socket. This API uses a promise to return the result.

> **NOTE:** 
> 
> It is recommended to use this API when the socket is connected. Otherwise, the corresponding traffic data cannot
> be queried after the socket is closed.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sockfd | number | Yes | FD of the socket to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the uplink traffic (in bytes) of the socket. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // In actual development, you need to first obtain it based on the socket you created.
statistics.getSockfdTxBytes(sockfd).then((stats: number) => {
  console.info(JSON.stringify(stats));
}).catch((err: BusinessError) => {
  console.error(JSON.stringify(err));
});
```
