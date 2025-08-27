# @ohos.net.connection (Network Connection Management)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

The **connection** module provides basic network management capabilities. With the APIs provided by this module, you can obtain the default active data network or the list of all active data networks, enable or disable the airplane mode, and obtain network capability information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Unless otherwise specified, the APIs of this module do not support concurrent calls.

## Modules to Import

```ts
import { connection } from '@kit.NetworkKit';
```

## connection.createNetConnection

createNetConnection(netSpecifier?: NetSpecifier, timeout?: number): NetConnection

Creates a **NetConnection** object, where [netSpecifier](#netspecifier) specifies the network, and **timeout** specifies the timeout duration in ms. **timeout** is configurable only when **netSpecifier** is specified. If neither of them is present, the default network is used.

**Note**: **createNetConnection** supports up to 2,000 registered callbacks. Exceeding this limit will result in a registration failure.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name      | Type                         | Mandatory| Description                                                        |
| ------------ | ----------------------------- | ---- | ------------------------------------------------------------ |
| netSpecifier | [NetSpecifier](#netspecifier) | No  | Network specifier, which specifies the network capability. If this parameter is left unspecified, the default network is used.                  |
| timeout      | number                        | No  | Timeout interval for obtaining the network specified by **netSpecifier**. The input value must be an uint32_t integer. This parameter is valid only when **netSpecifier** is present. The default value is **0**.|

**Return value**

| Type                           | Description                |
| ------------------------------- | -------------------- |
| [NetConnection](#netconnection) | Handle of the network specified by **netSpecifier**.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';

// Use the default network. No parameter needs to be passed.
let netConnection = connection.createNetConnection();

// Use the cellular network. Pass in network capabilities as needed. If the timeout parameter is not present, the value is 0, which indicates no timeout limit.
let netConnectionCellular = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_CELLULAR]
  }
});
```

## connection.getDefaultNet

getDefaultNet(callback: AsyncCallback\<NetHandle>): void

Obtains the default active data network. This API uses an asynchronous callback to return the result. You can use [getNetCapabilities](#connectiongetnetcapabilities) to obtain information such as the network type and capabilities.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<[NetHandle](#nethandle)> | Yes  | Callback used to return the result. If the default activated data network is obtained successfully, **error** is **undefined** and **data** is the default activated data network. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.                 |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet((error: BusinessError, data: connection.NetHandle) => {
  if (error) {
    console.error(`Failed to get default net. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data " + JSON.stringify(data));
});
```

## connection.getDefaultNet

getDefaultNet(): Promise\<NetHandle>

Obtains the default active data network. This API uses a promise to return the result. You can use [getNetCapabilities](#connectiongetnetcapabilities) to obtain information such as the network type and capabilities.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                             | Description                                 |
| --------------------------------- | ------------------------------------- |
| Promise\<[NetHandle](#nethandle)> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                        |
| ------- | -------------------------------- |
| 201     | Permission denied.               |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.           |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

## connection.getDefaultNetSync<sup>9+</sup>

getDefaultNetSync(): NetHandle

Obtains the default active data network in synchronous mode. You can use [getNetCapabilities](#connectiongetnetcapabilities) to obtain information such as the network type and capabilities.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type     | Description                              |
| --------- | ---------------------------------- |
| [NetHandle](#nethandle) | Handle of the default active data network.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                        |
| ------- | -------------------------------- |
| 201     | Permission denied.               |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.           |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getDefaultNetSync();
```


## connection.setAppHttpProxy<sup>11+</sup>

setAppHttpProxy(httpProxy: HttpProxy): void

Sets the application-level HTTP proxy configuration.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                                        | Mandatory| Description            |
| --------- | ------------------------------------------------------------ | ---- | ---------------- |
| httpProxy | [HttpProxy](#httpproxy10)                                      | Yes  | Application-level HTTP proxy configuration.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                      |
| ------- | -----------------------------  |
| 401     | Parameter error.               |
| 2100001 | Invalid http proxy.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let exclusionStr = "192.168,baidu.com";
let exclusionArray = exclusionStr.split(',');
connection.setAppHttpProxy({
  host: "192.168.xx.xxx",
  port: 8080,
  exclusionList: exclusionArray
} as connection.HttpProxy);
```

## connection.getDefaultHttpProxy<sup>10+</sup>

getDefaultHttpProxy(callback: AsyncCallback\<HttpProxy>): void

Obtains the default HTTP proxy configuration of the network. If the global proxy is set, the global HTTP proxy configuration is returned. If [setAppNet](#connectionsetappnet9) is used to bind the application to the network specified by [NetHandle](#nethandle), the HTTP proxy configuration of this network is returned. In other cases, the HTTP proxy configuration of the default network is returned. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<[HttpProxy](#httpproxy10)> | Yes  | Callback used to return the result. If the global HTTP proxy configuration of the network is obtained successfully, **error** is **undefined** and **data** is the global HTTP proxy configuration. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md).

| ID| Error Message                                    |
| -------- | -------------------------------------------- |
| 2100002  | Failed to connect to the service.            |
| 2100003  | System internal error.                       |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultHttpProxy((error: BusinessError, data: connection.HttpProxy) => {
  if (error) {
    console.error(`Failed to get default http proxy. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.log("Succeeded to get data" + JSON.stringify(data));
});
```

## connection.getDefaultHttpProxy<sup>10+</sup>

getDefaultHttpProxy(): Promise\<HttpProxy>

Obtains the default HTTP proxy configuration of the network. If the global proxy is set, the global HTTP proxy configuration is returned. If [setAppNet](#connectionsetappnet9) is used to bind the application to the network specified by [NetHandle](#nethandle), the HTTP proxy configuration of this network is returned. In other cases, the HTTP proxy configuration of the default network is returned. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                            | Description                                     |
| -------------------------------- | ----------------------------------------- |
| Promise<[HttpProxy](#httpproxy10)> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md).

| ID| Error Message                                    |
| -------- | -------------------------------------------- |
| 2100002  | Failed to connect to the service.            |
| 2100003  | System internal error.                       |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultHttpProxy().then((data: connection.HttpProxy) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.info(JSON.stringify(error));
});
```

## connection.getAppNet<sup>9+</sup>

getAppNet(callback: AsyncCallback\<NetHandle>): void

Obtains information about the network bound to an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<[NetHandle](#nethandle)> | Yes  | Callback used to return the result. If information about the network bound to the application is successfully obtained, **error** is **undefined** and **data** is the obtained network information. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 401     | Parameter error.                 |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAppNet((error: BusinessError, data: connection.NetHandle) => {
  if (error) {
    console.error(`Failed to get App net. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```

## connection.getAppNet<sup>9+</sup>

getAppNet(): Promise\<NetHandle>

Obtains information about the network bound to an application. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                             | Description                                 |
| --------------------------------- | ------------------------------------- |
| Promise\<[NetHandle](#nethandle)> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAppNet().then((data: connection.NetHandle) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.info(JSON.stringify(error));
});
```

## connection.getAppNetSync<sup>10+</sup>

getAppNetSync(): NetHandle

Obtains information about the network bound to an application. This API returns the result synchronously.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type     | Description                              |
| --------- | ---------------------------------- |
| [NetHandle](#nethandle) | Data network bound to the application.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getAppNetSync();
```

## connection.setAppNet<sup>9+</sup>

setAppNet(netHandle: NetHandle, callback: AsyncCallback\<void>): void

Binds an application to the network specified by **netHandle**, so that the application can access the external network only through this network, so that the application can access the external network only through this network. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description                                                        |
| --------- | ----------------------- | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle) | Yes  | Handle of the data network.                                            |
| callback  | AsyncCallback\<void>    | Yes  | Callback used to return the result. If the application is successfully bound to the specified network, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet((error: BusinessError, netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  connection.setAppNet(netHandle, (error: BusinessError, data: void) => {
    if (error) {
      console.error(`Failed to get default net. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

## connection.setAppNet<sup>9+</sup>

setAppNet(netHandle: NetHandle): Promise\<void\>

Binds an application to the network specified by **netHandle**, so that the application can access the external network only through this network. This API uses a promise to return the result. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                                        | Mandatory| Description            |
| --------- | ------------------------------------------------------------ | ---- | ---------------- |
| netHandle | [NetHandle](#nethandle)                                      | Yes  | Handle of the data network.|

**Return value**

| Type                                       | Description                         |
| ------------------------------------------- | ----------------------------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }

  connection.setAppNet(netHandle).then(() => {
    console.log("success");
  }).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  })
});
```

## connection.getAllNets

getAllNets(callback: AsyncCallback&lt;Array&lt;NetHandle&gt;&gt;): void

Obtains the list of all connected networks. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[NetHandle](#nethandle)&gt;&gt; | Yes| Callback used to return the result. If the list of all connected networks is obtained successfully, **error** is **undefined** and **data** is the list of activated data networks. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.                 |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
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

## connection.getAllNets

getAllNets(): Promise&lt;Array&lt;NetHandle&gt;&gt;

Obtains the list of all connected networks. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[NetHandle](#nethandle)&gt;&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getAllNets().then((data: connection.NetHandle[]) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

## connection.getAllNetsSync<sup>10+</sup>

getAllNetsSync(): Array&lt;NetHandle&gt;

Obtains the list of all connected networks. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type     | Description                              |
| --------- | ---------------------------------- |
| Array&lt;[NetHandle](#nethandle)&gt; | List of all connected data networks.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getAllNetsSync();
```

## connection.getConnectionProperties

getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback\<ConnectionProperties>): void

Obtains connection properties of the network specified by **netHandle**. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                                        | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle)                                      | Yes  | Handle of the data network.                                            |
| callback  | AsyncCallback\<[ConnectionProperties](#connectionproperties)> | Yes  | Callback used to return the result. If the connection properties of the network specified by **netHandle** is obtained successfully, **error** is **undefined** and **data** is the obtained network connection information. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  connection.getConnectionProperties(netHandle, (error: BusinessError, data: connection.ConnectionProperties) => {
    if (error) {
      console.error(`Failed to get connection properties. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  })
});
```

## connection.getConnectionProperties

getConnectionProperties(netHandle: NetHandle): Promise\<ConnectionProperties>

Obtains connection properties of the network specified by **netHandle**. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description            |
| --------- | ----------------------- | ---- | ---------------- |
| netHandle | [NetHandle](#nethandle) | Yes  | Handle of the data network.|

**Return value**

| Type                                                   | Description                             |
| ------------------------------------------------------- | --------------------------------- |
| Promise\<[ConnectionProperties](#connectionproperties)> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }

  connection.getConnectionProperties(netHandle).then((data: connection.ConnectionProperties) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  })
});
```

## connection.getConnectionPropertiesSync<sup>10+</sup>

getConnectionPropertiesSync(netHandle: NetHandle): ConnectionProperties

Obtains network connection information based on the specified **netHandle**.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description            |
| --------- | ----------------------- | ---- | ---------------- |
| netHandle | [NetHandle](#nethandle) | Yes  | Handle of the data network.|

**Return value**

| Type                                                   | Description                             |
| ------------------------------------------------------- | --------------------------------- |
| [ConnectionProperties](#connectionproperties) | Network connection information.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netHandle: connection.NetHandle;
let connectionproperties: connection.ConnectionProperties;

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  netHandle = connection.getDefaultNetSync();
  connectionproperties = connection.getConnectionPropertiesSync(netHandle);
  console.info("Succeeded to get connectionproperties: " + JSON.stringify(connectionproperties));
});

```

## connection.getNetCapabilities

getNetCapabilities(netHandle: NetHandle, callback: AsyncCallback\<NetCapabilities>): void

Obtains capability information of the network specified by **netHandle**. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                               | Mandatory| Description                                                        |
| --------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle)                             | Yes  | Handle of the data network.                                            |
| callback  | AsyncCallback\<[NetCapabilities](#netcapabilities)> | Yes  | Callback used to return the result. If the capability information of the network specified by **netHandle** is obtained successfully, **error** is **undefined** and **data** is the obtained network capability information. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  connection.getNetCapabilities(netHandle, (error: BusinessError, data: connection.NetCapabilities) => {
    if (error) {
      console.error(`Failed to get net capabilities. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  })
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
});
```

## connection.getNetCapabilities

getNetCapabilities(netHandle: NetHandle): Promise\<NetCapabilities>

Obtains capability information of the network specified by **netHandle**. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description            |
| --------- | ----------------------- | ---- | ---------------- |
| netHandle | [NetHandle](#nethandle) | Yes  | Handle of the data network.|

**Return value**

| Type                                         | Description                             |
| --------------------------------------------- | --------------------------------- |
| Promise\<[NetCapabilities](#netcapabilities)> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  connection.getNetCapabilities(netHandle).then((data: connection.NetCapabilities) => {
      console.info("Succeeded to get data: " + JSON.stringify(data));
  })
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
});
```

## connection.getNetCapabilitiesSync<sup>10+</sup>

getNetCapabilitiesSync(netHandle: NetHandle): NetCapabilities

Obtains capability information of the network specified by **netHandle**. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description            |
| --------- | ----------------------- | ---- | ---------------- |
| netHandle | [NetHandle](#nethandle) | Yes  | Handle of the data network.|

**Return value**

| Type                                         | Description                             |
| --------------------------------------------- | --------------------------------- |
| [NetCapabilities](#netcapabilities) | Network capability information.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netHandle: connection.NetHandle;
let getNetCapabilitiesSync: connection.NetCapabilities;

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }

  getNetCapabilitiesSync = connection.getNetCapabilitiesSync(netHandle);
  console.info("Succeeded to get net capabilities sync: " + JSON.stringify(getNetCapabilitiesSync));
});

```

## connection.isDefaultNetMetered<sup>9+</sup>

isDefaultNetMetered(callback: AsyncCallback\<boolean>): void

Checks whether the data traffic over the current network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                  |
| -------- | ----------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback\<boolean> | Yes  | Callback used to return the result. The value **true** indicates that the data traffic over the current network is metered, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.                 |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.isDefaultNetMetered((error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.log('data: ' + data);
});
```

## connection.isDefaultNetMetered<sup>9+</sup>

isDefaultNetMetered(): Promise\<boolean>

Checks whether the data traffic over the current network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type             | Description                                           |
| ----------------- | ----------------------------------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the data traffic over the current network is metered, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                        |
| ------- | -------------------------------- |
| 201     | Permission denied.               |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.           |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.isDefaultNetMetered().then((data: boolean) => {
  console.log('data: ' + data);
});
```

## connection.isDefaultNetMeteredSync<sup>10+</sup>

isDefaultNetMeteredSync(): boolean

Checks whether the data traffic over the current network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type             | Description                                           |
| ----------------- | ----------------------------------------------- |
| boolean | Boolean value indicating whether data traffic over the current network is metered. The value **true** indicates that the data traffic is metered, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                        |
| ------- | -------------------------------- |
| 201     | Permission denied.               |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.           |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let isMetered = connection.isDefaultNetMeteredSync();
```

## connection.hasDefaultNet

hasDefaultNet(callback: AsyncCallback\<boolean>): void

Checks whether the default data network is activated. This API uses an asynchronous callback to return the result. You can use [getDefaultNet](#connectiongetdefaultnet) to obtain the default data network, if any.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                  |
| -------- | ----------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback\<boolean> | Yes  | Callback used to return the result. The value **true** indicates that the default data network is activated, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.hasDefaultNet((error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.log('data: ' + data);
});
```

## connection.hasDefaultNet

hasDefaultNet(): Promise\<boolean>

Checks whether the default data network is activated. This API uses a promise to return the result. You can use [getDefaultNet](#connectiongetdefaultnet) to obtain the default data network, if any.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type             | Description                                           |
| ----------------- | ----------------------------------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the default data network is activated, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.hasDefaultNet().then((data: boolean) => {
  console.log('data: ' + data);
});
```

## connection.hasDefaultNetSync<sup>10+</sup>

hasDefaultNetSync(): boolean

Checks whether the default data network is activated. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type             | Description                                           |
| ----------------- | ----------------------------------------------- |
| boolean | Boolean value indicating whether the default data network is activated. The value **true** indicates that the default data network is activated, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let isDefaultNet = connection.hasDefaultNetSync();
```


## connection.reportNetConnected

reportNetConnected(netHandle: NetHandle, callback: AsyncCallback&lt;void&gt;): void

Reports a network connection event to the network management module. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| netHandle | [NetHandle](#nethandle) | Yes| Handle of the data network. For details, see [NetHandle](#nethandle).|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the network status is reported successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle, (error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
});
```

## connection.reportNetConnected

reportNetConnected(netHandle: NetHandle): Promise\<void\>

Reports a network connection event to the network management module. This API uses a promise to return the result.

**Permission required**: ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| netHandle | [NetHandle](#nethandle) | Yes| Handle of the data network. For details, see [NetHandle](#nethandle).|

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetConnected(netHandle).then(() => {
    console.log(`report success`);
  });
});
```

## connection.reportNetDisconnected

reportNetDisconnected(netHandle: NetHandle, callback: AsyncCallback&lt;void&gt;): void

Reports a network disconnection event to the network management module. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| netHandle | [NetHandle](#nethandle) | Yes| Handle of the data network. For details, see [NetHandle](#nethandle).|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the network status is reported successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet((error: BusinessError, netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  connection.reportNetDisconnected(netHandle, (error: BusinessError, data: void) => {
    if (error) {
      console.error(`Failed to get default net. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("report success");
  });
});
```

## connection.reportNetDisconnected

reportNetDisconnected(netHandle: NetHandle): Promise&lt;void&gt;

Reports a network disconnection event to the network management module. This API uses a promise to return the result.

**Permission required**: ohos.permission.GET_NETWORK_INFO and ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| netHandle | [NetHandle](#nethandle) | Yes| Handle of the data network. For details, see [NetHandle](#nethandle).|

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  connection.reportNetDisconnected(netHandle).then( () => {
    console.log(`report success`);
  });
});
```

## connection.getAddressesByName

getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void

Obtains all IP addresses by using the specified network to resolve the host name. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| host     | string                                            | Yes  | Host name to resolve.                                          |
| callback | AsyncCallback\<Array\<[NetAddress](#netaddress)>> | Yes  | Callback used to return the result. If all IP addresses are successfully obtained, **error** is **undefined**, and **data** is the list of all obtained IP addresses. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAddressesByName("xxxx", (error: BusinessError, data: connection.NetAddress[]) => {
  if (error) {
    console.error(`Failed to get addresses. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

## connection.getAddressesByName

getAddressesByName(host: string): Promise\<Array\<NetAddress\>\>

Obtains all IP addresses by using the specified network to resolve the host name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| host   | string | Yes  | Host name to resolve.|

**Return value**

| Type                                       | Description                         |
| ------------------------------------------- | ----------------------------- |
| Promise\<Array\<[NetAddress](#netaddress)>> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getAddressesByName("xxxx").then((data: connection.NetAddress[]) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

## connection.addCustomDnsRule<sup>11+</sup>

addCustomDnsRule(host: string, ip: Array\<string\>, callback: AsyncCallback\<void\>): void

Adds custom DNS rules for the specified host of the current application. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| host     | string               | Yes  | Name of the custom host.                                    |
| ip       | Array\<string>       | Yes  | List of IP addresses mapped to the host name.                                  |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the mapping is added successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.addCustomDnsRule("xxxx", ["xx.xx.xx.xx","xx.xx.xx.xx"], (error: BusinessError, data: void) => {
  if (error) {
    console.error(`Failed to get add custom dns rule. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```

## connection.addCustomDnsRule<sup>11+</sup>

addCustomDnsRule(host: string, ip: Array\<string\>): Promise\<void\>

Adds custom DNS rules for the specified host of the current application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type          | Mandatory| Description                      |
| ------ | -------------- | ---- | -------------------------- |
| host   | string         | Yes  | Name of the custom host.  |
| ip     | Array\<string> | Yes  | List of IP addresses mapped to the host name.|

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.addCustomDnsRule("xxxx", ["xx.xx.xx.xx","xx.xx.xx.xx"]).then(() => {
    console.info("success");
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
})
```

## connection.removeCustomDnsRule<sup>11+</sup>

removeCustomDnsRule(host: string, callback: AsyncCallback\<void\>): void

Removes the custom DNS rules of the specified host from the current application. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| host     | string               | Yes  | Name of the host for which DNS rules are to be deleted.                             |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the DNS rules are removed successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.removeCustomDnsRule("xxxx", (error: BusinessError, data: void) => {
  if (error) {
    console.error(`Failed to remove custom dns rule. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```

## connection.removeCustomDnsRule<sup>11+</sup>

removeCustomDnsRule(host: string): Promise\<void\>

Removes the custom DNS rules of the specified host from the current application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| host   | string | Yes  | Name of the host for which DNS rules are to be deleted.|

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.removeCustomDnsRule("xxxx").then(() => {
    console.log("success");
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
})
```

## connection.clearCustomDnsRules<sup>11+</sup>

clearCustomDnsRules(callback: AsyncCallback\<void\>): void

Removes all custom DNS rules from the current application. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If all the DNS rules are removed successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                          |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.clearCustomDnsRules((error: BusinessError, data: void) => {
  if (error) {
    console.error(`Failed to clear custom dns rules. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```

## connection.clearCustomDnsRules<sup>11+</sup>

clearCustomDnsRules(): Promise\<void\>

Removes all custom DNS rules from the current application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| Promise\<void\>        | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.clearCustomDnsRules().then(() => {
    console.log("success");
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
})
```

## connection.setPacUrl<sup>15+</sup>

setPacUrl(pacUrl: string): void

Sets the URL of the system-level Proxy Auto Config (PAC) script.

**Required permissions**: ohos.permission.SET_PAC_URL

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| pacUrl   | string                                            | Yes  | URL of the PAC script. Note that this URL will not be verified by the API.            |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let pacUrl = "xxx";
connection.setPacUrl(pacUrl);
```

## connection.getPacUrl<sup>15+</sup>

getPacUrl(): string

Obtains the URL of the system-level PAC script.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| string        | URL of the PAC script. If the PAC script does not exist, error code 2100003 is reported. |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

let pacUrl = connection.getPacUrl();
```

## connection.setNetExtAttribute<sup>20+</sup>

setNetExtAttribute(netHandle: NetHandle, netExtAttribute: string): Promise\<void\>

Sets extended attributes of the network specified by **netHandle** to indicate its security level. This API uses a promise to return the result.

> **NOTE**
> Currently, this API is available only for PCs.

**Required permissions**: ohos.permission.SET_NET_EXT_ATTRIBUTE

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                             | Mandatory| Description                                                        |
| --------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle)                                         | Yes  | Handle of the data network.          |
| netExtAttribute | string                                      | Yes  | Extended network attributes.                                        |

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let netExtAttribute: string = "xxx";
  connection.setNetExtAttribute(netHandle, netExtAttribute).then(() => {
    console.info("setNetExtAttribute success");
  }).catch((error: BusinessError) => {
    console.error("setNetExtAttribute failed, err: " + error.code);
  })
});
```

## connection.setNetExtAttributeSync<sup>20+</sup>

setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void

Sets extended attributes of the network specified by **netHandle** to indicate its security level. This API returns the result synchronously.

> **NOTE**
> Currently, this API is available only on PCs.

**Required permissions**: ohos.permission.SET_NET_EXT_ATTRIBUTE

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                             | Mandatory| Description                                                        |
| --------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle)                  | Yes  | Handle of the data network.            |
| netExtAttribute | string                             | Yes  | Extended network attributes.     |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netExtAttribute: string = "xxx";
let netHandle = connection.getDefaultNetSync();
if (netHandle.netId != 0) {
  connection.setNetExtAttributeSync(netHandle, netExtAttribute);
}
```

## connection.getNetExtAttribute<sup>20+</sup>

getNetExtAttribute(netHandle: NetHandle): Promise\<string\>

Obtains the extended attributes of the network specified by **netHandle** to determine its security level. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                     | Mandatory| Description                          |
| --------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle)                | Yes  | Handle of the data network.            |

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| Promise\<string\> | Promise used to return the result.  |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  connection.getNetExtAttribute(netHandle).then((netExtAttribute: string) => {
    console.info("getNetExtAttribute: " + netExtAttribute);
  }).catch((error: BusinessError) => {
    console.error("getNetExtAttribute failed, err: " + error.code);
  })
});
```

## connection.getNetExtAttributeSync<sup>20+</sup>

getNetExtAttributeSync(netHandle: NetHandle): string

Obtains the extended attributes of the network specified by **netHandle** to determine its security level. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                             | Mandatory| Description                                                        |
| --------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| netHandle | [NetHandle](#nethandle)                   | Yes  | Handle of the data network.        |

**Return value**

| Type  | Description                    |
| ------ | ----------------------- |
| string | Extended network attributes.|


**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netHandle = connection.getDefaultNetSync();
if (netHandle.netId != 0) {
  let netExtAttribute: string = connection.getNetExtAttributeSync(netHandle);
  console.info("getNetExtAttribute: " + netExtAttribute);
}
```

## NetConnection

Represents the network connection handle.

> **NOTE**
>
>(1) When the network transitions from unavailable to available, the **netAvailable**, **netCapabilitiesChange**, and **netConnectionPropertiesChange** events are triggered.
>
>(2) If the network transitions from available to unavailable after a **netAvailable** event is received, a **netLost** event is triggered.
>
>(3) If no **netAvailable** event is received, a **netUnavailable** event is directly triggered.
>
>(4) When the network transitions from Wi-Fi to cellular, a **netLost** event is first triggered to indicate that the Wi-Fi network is lost and then a **netAvailable** event is triggered to indicate that the cellular network is available.

### register

register(callback: AsyncCallback\<void>): void

Registers a listener for network status changes.

**Note**: After using this API, you need to call **unregister** to cancel the registration in a timely manner.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If a listener for network status changes is registered successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID|                       Error Message                      |
| ------- | ---------------------------------------------------- |
| 201     | Permission denied.                                   |
| 401     | Parameter error.                                     |
| 2100002 | Failed to connect to the service.                    |
| 2100003 | System internal error.                               |
| 2101008 | The callback already exists.                         |
| 2101022 | The number of requests exceeded the maximum allowed. |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### unregister

unregister(callback: AsyncCallback\<void>): void

Unregisters the listener for network status changes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If a listener for network status changes is unregistered successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 401     | Parameter error.                  |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |
| 2101007 | The callback does not exist.      |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netCon: connection.NetConnection = connection.createNetConnection();
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### on('netAvailable')

on(type: 'netAvailable', callback: Callback\<NetHandle>): void

Registers a listener for **netAvailable** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                              | Mandatory| Description                                                        |
| -------- | ---------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                             | Yes  | Event type. This field has a fixed value of **netAvailable**.<br>**netAvailable**: event indicating that the data network is available.|
| callback | Callback\<[NetHandle](#nethandle)> | Yes  | Callback used to return the network handle.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a NetConnection object.
let netCon: connection.NetConnection = connection.createNetConnection();

// Use the register API to subscribe to network status change events.
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// Use the register API to subscribe to netAvailable events.
netCon.on('netAvailable', (data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// Use the unregister API to unsubscribe from netAvailable events.
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### on('netBlockStatusChange')

on(type: 'netBlockStatusChange', callback: Callback\<NetBlockStatusInfo>): void

Registers a listener for **netBlockStatusChange** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **netBlockStatusChange**.<br>**netBlockStatusChange**: event indicating a change in the network blocking status.|
| callback | Callback<[NetBlockStatusInfo](#netblockstatusinfo11)>        | Yes  | Callback used to return the result.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a NetConnection object.
let netCon: connection.NetConnection = connection.createNetConnection();

// Use the register API to subscribe to network status change events.
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// Subscribe to netBlockStatusChange events. Before that, make sure you have called the register API to add a listener.
netCon.on('netBlockStatusChange', (data: connection.NetBlockStatusInfo) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// Use the unregister API to remove the listener for netBlockStatusChange events.
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### on('netCapabilitiesChange')

on(type: 'netCapabilitiesChange', callback: Callback\<NetCapabilityInfo\>): void

Registers a listener for **netCapabilitiesChange** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **netCapabilitiesChange**.<br>**netCapabilitiesChange**: event indicating that the network capabilities have changed.|
| callback | Callback<[NetCapabilityInfo](#netcapabilityinfo10)>          | Yes  | Callback used to return the network handle (**netHandle**) and capability information (**netCap**).|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a NetConnection object.
let netCon: connection.NetConnection = connection.createNetConnection();

// Use the register API to subscribe to network status change events.
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// Subscribe to netCapabilitiesChange events. Before that, make sure you have called the register API to add a listener.
netCon.on('netCapabilitiesChange', (data: connection.NetCapabilityInfo) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// Unsubscribe from netCapabilitiesChange events.
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### on('netConnectionPropertiesChange')

on(type: 'netConnectionPropertiesChange', callback: Callback\<NetConnectionPropertyInfo\>): void

Registers a listener for **netConnectionPropertiesChange** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. This field has a fixed value of **netConnectionPropertiesChange**.<br>**netConnectionPropertiesChange**: event indicating that network connection properties have changed.|
| callback | Callback<[NetConnectionPropertyInfo](#netconnectionpropertyinfo11)> | Yes  | Callback used to return the result.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a NetConnection object.
let netCon: connection.NetConnection = connection.createNetConnection();

// Use the register API to subscribe to network status change events.
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// Subscribe to netConnectionPropertiesChange events. Before that, make sure you have called the register API to add a listener.
netCon.on('netConnectionPropertiesChange', (data: connection.NetConnectionPropertyInfo) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// Use the unregister API to remove the listener for netConnectionPropertiesChange events.
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### on('netLost')

on(type: 'netLost', callback: Callback\<NetHandle>): void

Registers a listener for **netLost** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                              | Mandatory| Description                                                        |
| -------- | ---------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                             | Yes  | Event type. This field has a fixed value of **netLost**.<br>**netLost**: event indicating that the network is interrupted or normally disconnected.|
| callback | Callback\<[NetHandle](#nethandle)> | Yes  | Callback used to return the result, which is a **netHandle** object.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a NetConnection object.
let netCon: connection.NetConnection = connection.createNetConnection();

// Use the register API to subscribe to network status change events.
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// Subscribe to netLost events. Before that, make sure you have called the register API to add a listener.
netCon.on('netLost', (data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});

// Use the unregister API to remove the listener for netLost events.
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

### on('netUnavailable')

on(type: 'netUnavailable', callback: Callback\<void>): void

Registers a listener for **netUnavailable** events. Before you call this API, make sure that you have called **register** to add a listener for network status changes. When the listener is no longer needed, call **unregister** to remove it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type           | Mandatory| Description                                                        |
| -------- | --------------- | ---- | ------------------------------------------------------------ |
| type     | string          | Yes  | Event type. This field has a fixed value of **netUnavailable**.<br>**netUnavailable**: event indicating that the network is unavailable.|
| callback | Callback\<void> | Yes  | Callback used to return the result, which is empty.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a NetConnection object.
let netCon: connection.NetConnection = connection.createNetConnection();

// Use the register API to subscribe to network status change events.
netCon.register((error: BusinessError) => {
  console.error(JSON.stringify(error));
});

// Subscribe to netUnavailable events. Before that, make sure you have called the register API to add a listener.
netCon.on('netUnavailable', () => {
  console.info("Succeeded to get unavailable net event");
});

// Use the unregister API to remove the listener for netUnavailable events.
netCon.unregister((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## NetHandle

Defines the handle of the data network.

Before invoking **NetHandle** APIs, call **getNetHandle** to obtain a **NetHandle** object.

**System capability**: SystemCapability.Communication.NetManager.Core

### Attributes

| Name   | Type  | Mandatory| Description                     |
| ------ | ------ | --- |------------------------- |
| netId  | number | Yes |  Network ID. The value **0** indicates no default network. Any other value must be greater than or equal to 100.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

### bindSocket<sup>9+</sup>

bindSocket(socketParam: TCPSocket \| UDPSocket, callback: AsyncCallback\<void>): void

Binds the TCPSocket or UDPSocket to the network specified by **NetHandle**. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name     | Type                    | Mandatory| Description                           |
| ----------- | ------------------------ | ---- | -------------------------------|
| socketParam | [TCPSocket](js-apis-socket.md#tcpsocket) \| [UDPSocket](js-apis-socket.md#udpsocket) | Yes| **TCPSocket** or **UDPSocket** object.|
| callback    | AsyncCallback\<void>      | Yes  | Callback used to return the result. If the **TCPSocket** or **UDPSocket** object is successfully bound to the current network, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface Data {
  message: ArrayBuffer,
  remoteInfo: socket.SocketRemoteInfo
}

  connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
  }
  let tcp : socket.TCPSocket = socket.constructTCPSocketInstance();
  let udp : socket.UDPSocket = socket.constructUDPSocketInstance();
  let socketType = "TCPSocket";
  if (socketType == "TCPSocket") {
    tcp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: Error) => {
      if (error) {
        console.error('bind fail');
        return;
      }
      netHandle.bindSocket(tcp, (error: BusinessError, data: void) => {
        if (error) {
          console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
          return;
        } else {
          console.info(JSON.stringify(data));
        }
      });
    });
  } else {
    let callback: (value: Data) => void = (value: Data) => {
      console.log("on message, message:" + value.message + ", remoteInfo:" + value.remoteInfo);
    };
    udp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      udp.on('message', (data: Data) => {
        console.info("Succeeded to get data: " + JSON.stringify(data));
      });
      netHandle.bindSocket(udp, (error: BusinessError, data: void) => {
        if (error) {
          console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
          return;
        } else {
          console.info(JSON.stringify(data));
        }
      });
    });
  }
})
```

### bindSocket<sup>9+</sup>

bindSocket(socketParam: TCPSocket \| UDPSocket): Promise\<void\>

Binds the TCPSocket or UDPSocket to the network specified by **NetHandle**. This API uses a promise to return the result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name         | Type                 | Mandatory | Description                          |
| --------------- | --------------------- | ---- | ------------------------------ |
| socketParam     | [TCPSocket](js-apis-socket.md#tcpsocket) \| [UDPSocket](js-apis-socket.md#udpsocket) | Yes  | **TCPSocket** or **UDPSocket** object.|

**Return value**

| Type          | Description                  |
| -------------- | ---------------------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface Data {
  message: ArrayBuffer,
  remoteInfo: socket.SocketRemoteInfo
}

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let tcp : socket.TCPSocket = socket.constructTCPSocketInstance();
  let udp : socket.UDPSocket = socket.constructUDPSocketInstance();
  let socketType = "TCPSocket";
  if (socketType == "TCPSocket") {
    tcp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: Error) => {
      if (error) {
        console.error('bind fail');
        return;
      }
      netHandle.bindSocket(tcp).then(() => {
        console.info("bind socket success");
      }).catch((error: BusinessError) => {
        console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
      });
    });
  } else {
    let callback: (value: Data) => void = (value: Data) => {
      console.log("on message, message:" + value.message + ", remoteInfo:" + value.remoteInfo);
    }
    udp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      udp.on('message', (data: Data) => {
        console.info("Succeeded to get data: " + JSON.stringify(data));
      });
      netHandle.bindSocket(udp).then(() => {
        console.info("bind socket success");
      }).catch((error: BusinessError) => {
        console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
      });
    });
  }
});
```

### getAddressesByName

getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>\>\): void

Obtains all IP addresses by using the network specified by **NetHandle** to resolve the host name. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| host     | string                                            | Yes  | Host name to resolve.                                          |
| callback | AsyncCallback\<Array\<[NetAddress](#netaddress)>> | Yes  | Callback used to return the result. If all IP addresses are successfully obtained, **error** is **undefined**, and **data** is the list of all obtained IP addresses. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "xxxx";
  netHandle.getAddressesByName(host, (error: BusinessError, data: connection.NetAddress[]) => {
    if (error) {
      console.error(`Failed to get addresses. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

### getAddressesByName

getAddressesByName(host: string): Promise\<Array\<NetAddress>>

Obtains all IP addresses by using the network specified by **NetHandle** to resolve the host name. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| host   | string | Yes  | Host name to resolve.|

**Return value**

| Type                                       | Description                         |
| ------------------------------------------- | ----------------------------- |
| Promise\<Array\<[NetAddress](#netaddress)>> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "xxxx";
  netHandle.getAddressesByName(host).then((data: connection.NetAddress[]) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

### getAddressByName

getAddressByName(host: string, callback: AsyncCallback\<NetAddress>): void

Obtains the first IP address by using the network specified by **NetHandle** to resolve the host name. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                                                        |
| -------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| host     | string                                    | Yes  | Host name to resolve.                                          |
| callback | AsyncCallback\<[NetAddress](#netaddress)> | Yes  | Callback used to return the result. If the first IP address is obtained successfully, **error** is **undefined**, and **data** is the first obtained IP address. Otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "xxxx";
  netHandle.getAddressByName(host, (error: BusinessError, data: connection.NetAddress) => {
    if (error) {
      console.error(`Failed to get address. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

### getAddressByName

getAddressByName(host: string): Promise\<NetAddress>

Obtains the first IP address by using the network specified by **NetHandle** to resolve the host name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INTERNET

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| host   | string | Yes  | Host name to resolve.|

**Return value**

| Type                               | Description                           |
| ----------------------------------- | ------------------------------- |
| Promise\<[NetAddress](#netaddress)> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                         |
| ------- | --------------------------------- |
| 201     | Permission denied.                |
| 401     | Parameter error.                  |
| 2100001 | Invalid parameter value.          |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error.            |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "xxxx";
  netHandle.getAddressByName(host).then((data: connection.NetAddress) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

## NetCap

Defines the network capability.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                 | Value  | Description                  |
| ------------------------ | ---- | ---------------------- |
| NET_CAPABILITY_MMS | 0 | The network can connect to the carrier's Multimedia Messaging Service Center (MMSC) to send and receive multimedia messages.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| NET_CAPABILITY_NOT_METERED | 11 | The network traffic is not metered.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| NET_CAPABILITY_INTERNET  | 12   | The network is capable of Internet access but the network connectivity is not successfully verified by the network management module. This capability is configured by the network provider. Your application can determine the network connectivity by **NET_CAPABILITY_VALIDATED** and **NET_CAPABILITY_CHECKING_CONNECTIVITY**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| NET_CAPABILITY_NOT_VPN | 15 | The network does not use a virtual private network (VPN).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| NET_CAPABILITY_VALIDATED | 16   | The network management module successfully connects to the Huawei Cloud address through this network. This capability is configured by the network management module.<br>Note: If the network management module fails to connect to the Huawei Cloud address, this flag is not available in the network capability, but this does not mean a complete loss in Internet access. Note that for a newly connected network, this value may not reflect the actual verification result as network connectivity verification is in progress. Your application can use **NET_CAPABILITY_CHECKING_CONNECTIVITY**<sup>12+</sup> to check whether network connectivity verification is in progress.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| NET_CAPABILITY_PORTAL<sup>12+</sup> | 17   | The network is found to have a captive portal and user login authentication is required. This capability is set by the connection management module.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| NET_CAPABILITY_CHECKING_CONNECTIVITY<sup>12+</sup> | 31   | The network management module is verifying the network connectivity. This flag remains valid until the network connectivity check is complete. During this period, the value of **NET_CAPABILITY_VALIDATED** may be incorrect. After the network connectivity check is complete, this flag is cleared and your application can determine the network connectivity by checking **NET_CAPABILITY_VALIDATED**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## NetBearType

Enumerates network types.

**System capability**: SystemCapability.Communication.NetManager.Core

|            Name        | Value  | Description       |
| ----------------------- | ---- | ---------- |
| BEARER_CELLULAR | 0    | Cellular network.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| BEARER_WIFI     | 1    | Wi-Fi network.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| BEARER_BLUETOOTH<sup>12+</sup> | 2    | Bluetooth network.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| BEARER_ETHERNET | 3    | Ethernet network.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| BEARER_VPN<sup>12+</sup>| 4    | VPN.  |

## HttpProxy<sup>10+</sup>

Represents the HTTP proxy configuration.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name   | Type  | Mandatory| Description                     |
| ------ | ------ | --- |------------------------- |
| host  | string | Yes |  Host name of the proxy server.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| port  | number | Yes |  Host port. The value range is \[0, 65535].<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| exclusionList  | Array\<string\> | Yes | List of the names of hosts that do not use a proxy. Host names can be domain names, IP addresses, or wildcards. The detailed matching rules are as follows:<br>- Domain name matching:<br>  - Exact match: The host name of the proxy server exactly matches any host name in the list.<br>  - Partial match: The host name of the proxy server contains any host name in the list.<br>For example, if **ample.com** is set in the host name list, **ample.com**, **www.ample.com**, and **ample.com:80** are matched, and **www.example.com** and **ample.com.org** are not matched.<br>- IP address matching: The host name of the proxy server exactly matches any IP address in the list.<br>- Both the domain name and IP address are added to the list for matching.<br>- A single asterisk (*) is the only valid wildcard. If the list contains only wildcards, the wildcards match all host names; that is, the HTTP proxy is disabled. A wildcard can only be added independently. It cannot be added to the list together with other domain names or IP addresses. Otherwise, the wildcard does not take effect.<br>- Host names are case insensitive.<br>- Protocol prefixes such as **http** and **https** are ignored during matching.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| username<sup>12+</sup>  | string | No|  Name of the user who uses the proxy.|
| password<sup>12+</sup>  | string | No|  Password of the user who uses the proxy.|

## NetSpecifier

Provides an instance that bears data network capabilities.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                    | Type                               | Mandatory | Description                                                        |
| ----------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| netCapabilities         | [NetCapabilities](#netcapabilities) |  Yes | Network transmission capabilities and bearer types of the data network.                               |
| bearerPrivateIdentifier | string                              |  No |  Network identifier. The identifier of the cellular network is **slot0** for SIM card 1 and **slot1** for SIM card 2. Since API version 12, you can pass the registered WLAN hotspot to the API to specify the WLAN network to be activated.|

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: wifiManager.WifiDeviceConfig = {
  ssid: "TEST",
  preSharedKey: "**********",
  securityType: wifiManager.WifiSecurityType.WIFI_SEC_TYPE_PSK
};
// Obtain the network ID of the registered WLAN through wifiManager.addCandidateConfig.
wifiManager.addCandidateConfig(config,(error,networkId) => {
 let netConnectionWlan = connection.createNetConnection({
   netCapabilities: {
     bearerTypes: [connection.NetBearType.BEARER_WIFI]
   },
   bearerPrivateIdentifier: `${networkId}`
 });
 netConnectionWlan.register((error: BusinessError) => {
   console.error(JSON.stringify(error));
 });
});
```

## NetCapabilityInfo<sup>10+</sup>

Provides an instance that bears data network capabilities.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                   | Type                                | Mandatory | Description                                                        |
| ----------------------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| netHandle               | [NetHandle](#nethandle)              |  Yes | Handle of the data network.                                               |
| netCap                  |  [NetCapabilities](#netcapabilities) |  Yes |  Network transmission capabilities and bearer types of the data network.                           |

## NetCapabilities

Defines the network capability set.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                 | Type                               | Mandatory| Description                    |
| --------------------- | ---------------------------------- | --- | ------------------------ |
| linkUpBandwidthKbps   | number                             |  No|  Uplink (device-to-network) bandwidth, in kbit/s. The value **0** indicates that the current network bandwidth cannot be evaluated.|
| linkDownBandwidthKbps | number                             |  No|  Downlink (network-to-device) bandwidth, in kbit/s. The value **0** indicates that the current network bandwidth cannot be evaluated.|
| networkCap            | Array\<[NetCap](#netcap)>           |  No|  Network capability.<br>**Atomic service API**: This API can be used in atomic services since API version 11.          |
| bearerTypes           | Array\<[NetBearType](#netbeartype)> |  Yes|  Network type. The array contains only one network type.<br>**Atomic service API**: This API can be used in atomic services since API version 11.     |

## NetConnectionPropertyInfo<sup>11+</sup>

Defines the network connection properties.

**System capability**: SystemCapability.Communication.NetManager.Core

### Attributes

| Name                |                          Type                       | Mandatory|         Description          |
| -------------------- | --------------------------------------------------- | ---- |----------------------- |
| netHandle            | [NetHandle](#nethandle)                             | Yes  |Data network handle.|
| connectionProperties | [ConnectionProperties](#connectionproperties)       | Yes  |Network connection properties.          |

## NetBlockStatusInfo<sup>11+</sup>

Obtains the network block status information.

**System capability**: SystemCapability.Communication.NetManager.Core

### Attributes

| Name                | Type                                 | Mandatory|            Description           |
| -------------------- | ------------------------------------- | --- |--------------------------- |
| netHandle            | [NetHandle](#nethandle)               | Yes  |Data network handle.  |
| blocked              | boolean                               | Yes  |The value **true** indicates that the network is congested, and the value **false** indicates the opposite.|

## ConnectionProperties

Defines the network connection properties.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name         |                Type                | Mandatory|               Description                    |
| ------------- | ----------------------------------- | ----|--------------------------------------- |
| interfaceName | string                              | Yes|Network interface card (NIC) name.                               |
| domains       | string                              | Yes|Domain name.                                   |
| linkAddresses | Array\<[LinkAddress](#linkaddress)> | Yes|Network link information.                               |
| routes        | Array\<[RouteInfo](#routeinfo)>     | Yes|Network route information.                               |
| dnses         | Array\<[NetAddress](#netaddress)>   | Yes|Network address. For details, see [NetAddress](#netaddress).|
| mtu           | number                              | Yes|Maximum transmission unit (MTU).                           |

## RouteInfo

Defines network route information.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name          | Type                       | Mandatory|     Description     |
| -------------- | --------------------------- | --- |-------------- |
| interface      | string                      | Yes|NIC name.      |
| destination    | [LinkAddress](#linkaddress) | Yes|Destination address.      |
| gateway        | [NetAddress](#netaddress)   | Yes|Gateway address.      |
| hasGateway     | boolean                     | Yes|Whether a gateway is available. The value **true** indicates that a gateway is available, and the value **false** indicates the opposite.    |
| isDefaultRoute | boolean                     | Yes|Whether the route is the default route. The value **true** indicates that the route is the default route, and the value **false** indicates the opposite.|
| isExcludedRoute<sup>20+</sup>| boolean                     | No|Whether the route is excluded. The value **true** indicates that the route is excluded, and the value **false** indicates the opposite.|

## LinkAddress

Defines network link information.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name        |           Type           | Mandatory|        Description        |
| ------------ | ------------------------- |---- |-------------------- |
| address      | [NetAddress](#netaddress) | Yes | Link address.          |
| prefixLength | number                    | Yes |Length of the link address prefix. |

## NetAddress

Defines a network address.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.NetManager.Core

|  Name  | Type  |Mandatory|            Description             |
| ------- | ------ | -- |---------------------------- |
| address | string | Yes|Network address.                      |
| family  | number | No|Address family identifier. The value is **1** for IPv4 and **2** for IPv6. The default value is **1**.|
| port    | number | No|Port number. The value range is \[0, 65535]. The default value is **0**. |

## HttpRequest

type HttpRequest = http.HttpRequest

Defines an HTTP request, which can be created using [http.createHttp](js-apis-http.md#httpcreatehttp).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Communication.NetStack

|       Type      |            Description            |
| ---------------- | --------------------------- |
| http.HttpRequest | HTTP request task. You need to obtain an HTTP request task before calling **HttpRequest** APIs .|

## TCPSocket

type TCPSocket = socket.TCPSocket

Defines a **TCPSocket** object, which can be created using [socket.constructTCPSocketInstance](js-apis-socket.md#socketconstructtcpsocketinstance7).

**System capability**: SystemCapability.Communication.NetStack

|       Type      |            Description            |
| ---------------- | --------------------------- |
| socket.TCPSocket | **TCPSocket** object.    |

## UDPSocket

type UDPSocket = socket.UDPSocket

Defines a **UDPSocket** object, which can be created using [socket.constructUDPSocketInstance](js-apis-socket.md#socketconstructudpsocketinstance).

**System capability**: SystemCapability.Communication.NetStack

|       Type      |            Description            |
| ---------------- | --------------------------- |
| socket.UDPSocket | **UDPSocket** object.    |
