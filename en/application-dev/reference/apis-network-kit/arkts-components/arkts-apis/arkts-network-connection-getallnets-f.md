# getAllNets

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getAllNets

```TypeScript
function getAllNets(callback: AsyncCallback<Array<NetHandle>>): void
```

Obtains the list of all connected networks. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NetHandle](arkts-network-connection-nethandle-i.md)&gt;&gt; | Yes | Callback used to return the result. If the list of all connected networks is obtained successfully, **error** is **undefined** and **data** is the list of activated networks. Otherwise, **error** is an error object.<br> Note: If Wi-Fi and cellular data are both enabled, and no application specifies the use of cellular data, only Wi-Fi is activated. In this case, only the **NetHandle** of Wi-Fi is returned. The NetHandle of Wi-Fi and cellular data can be obtained at the same time only when a specific application enables the cellular network. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAllNets((error: BusinessError, data: connection.NetHandle[]) => {
  if (error) {
    console.error(`Failed to get all nets. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```


<a id="getallnets-1"></a>

## getAllNets

```TypeScript
function getAllNets(): Promise<Array<NetHandle>>
```

Obtains the list of all connected networks. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NetHandle](arkts-network-connection-nethandle-i.md)&gt;&gt; | Promise used to return the list of activated networks. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getAllNets().then((data: connection.NetHandle[]) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```
