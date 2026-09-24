# reportNetConnected

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## reportNetConnected

```TypeScript
function reportNetConnected(netHandle: NetHandle, callback: AsyncCallback<void>): void
```

Reports the network availability to the network management module. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is used by the browser to connect to the portal network. After the network authentication is successful,
> the browser reports the network connection success to the network management module. The network management
> module then triggers network detection and updates the network status.
> **Permission required**: ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. For details, see [NetHandle](arkts-network-connection-nethandle-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the network status is reported successfully, **error** is **undefined**. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle, (error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
});
```


<a id="reportnetconnected-1"></a>

## reportNetConnected

```TypeScript
function reportNetConnected(netHandle: NetHandle): Promise<void>
```

Reports that the network is available to the network management module. This API uses a promise to return the result.

**Permission required**: ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. For details, see [NetHandle](arkts-network-connection-nethandle-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle).then(() => {
    console.info(`report success`);
  });
});
```
