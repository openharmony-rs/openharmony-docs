# getDefaultHttpProxy

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getDefaultHttpProxy

```TypeScript
function getDefaultHttpProxy(callback: AsyncCallback<HttpProxy>): void
```

Obtains the default HTTP proxy configuration of the network. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - If the global proxy is set, the global proxy configuration is returned.
> 
> - If [setAppNet](arkts-network-connection-setappnet-f.md) is used to bind the application to the network specified by [NetHandle](arkts-network-connection-nethandle-i.md), the HTTP proxy configuration of this network is returned. In other cases, the HTTP proxy configuration of the default network is returned.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HttpProxy](arkts-network-connection-httpproxy-i.md)&gt; | Yes | Callback used to return the result. If the global HTTP proxy configuration of the network is obtained successfully, **error** is **undefined** and **data** is the global HTTP proxy configuration. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultHttpProxy((error: BusinessError, data: connection.HttpProxy) => {
  if (error) {
    console.error(`Failed to get default http proxy. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data" + JSON.stringify(data));
});
```

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultHttpProxy().then((data: connection.HttpProxy) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.info(JSON.stringify(error));
});
```


## getDefaultHttpProxy

```TypeScript
function getDefaultHttpProxy(): Promise<HttpProxy>
```

Obtains the default HTTP proxy configuration of the network. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If the global proxy is set, the global proxy configuration is returned.
> 
> - If [setAppNet](arkts-network-connection-setappnet-f.md) is used to bind the application to the network specified by [NetHandle](arkts-network-connection-nethandle-i.md), the HTTP proxy configuration of this network is returned. In other cases, the HTTP proxy configuration of the default network is returned.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HttpProxy](arkts-network-connection-httpproxy-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

See [getDefaultHttpProxy](#getdefaulthttpproxy)
