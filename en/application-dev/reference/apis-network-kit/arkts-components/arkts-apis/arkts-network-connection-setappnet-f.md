# setAppNet

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setAppNet

```TypeScript
function setAppNet(netHandle: NetHandle, callback: AsyncCallback<void>): void
```

Binds an application to the network specified by **netHandle**, so that the application can access the external network only through this network. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the application is successfully bound to the specified network, **error** is **undefined**. Otherwise, **error** is an error object. |

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
If an application is bound to a Wi-Fi network and the Wi-Fi signal is weak or the network is disconnected, the application cannot access the Internet if it is not unbound.

The following example binds the application to a Wi-Fi network. It uses the [on('netAvailable')](arkts-network-connection-netconnection-i.md#onnetavailable) API to bind the application when the Wi-Fi network is available, and the [on('netLost')](arkts-network-connection-netconnection-i.md#onnetlost) API to unbind the application and switch to the default network when the Wi-Fi network is unavailable.
```


## setAppNet

```TypeScript
function setAppNet(netHandle: NetHandle): Promise<void>
```

Binds an application to the network specified by **netHandle**, so that the application can access the external network only through this network. This API uses a promise to return the result. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

See [setAppNet](#setappnet)
