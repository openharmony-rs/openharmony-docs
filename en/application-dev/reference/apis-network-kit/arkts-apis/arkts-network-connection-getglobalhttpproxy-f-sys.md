# getGlobalHttpProxy (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getGlobalHttpProxy

```TypeScript
function getGlobalHttpProxy(callback: AsyncCallback<HttpProxy>): void
```

Obtains the global network proxy configuration information. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HttpProxy](arkts-network-connection-httpproxy-i.md)&gt; | Yes | Callback used to return the result. If the global HTTP proxy configuration of the network is obtained successfully, **error** is **undefined** and **data** is the global HTTP proxy configuration. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getGlobalHttpProxy((error: BusinessError, data: connection.HttpProxy) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


<a id="getglobalhttpproxy-1"></a>

## getGlobalHttpProxy

```TypeScript
function getGlobalHttpProxy(): Promise<HttpProxy>
```

Obtains the global network proxy configuration information. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HttpProxy](arkts-network-connection-httpproxy-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getGlobalHttpProxy().then((data: connection.HttpProxy) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```
