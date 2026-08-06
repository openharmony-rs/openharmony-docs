# @ohos.net.connection (Network Connection Management) (System API)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:50:35.595Z pushedAt=2026-06-26T03:00:41.289Z -->

The network connection management module provides basic network capabilities. You can obtain the default active data network or the list of all active data networks, enable or disable the airplane mode, and obtain network capability information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.net.connection (Network Connection Management)](js-apis-net-connection.md).

## Modules to Import

```ts
import { connection } from '@kit.NetworkKit';
```


## connection.getGlobalHttpProxy<sup>10+</sup>

getGlobalHttpProxy(callback: AsyncCallback\<HttpProxy>): void

Obtains the global network proxy configuration information. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<[HttpProxy](js-apis-net-connection.md#httpproxy10)> | Yes  | Callback used to return the result. If the global HTTP proxy configuration of the network is obtained successfully, **error** is **undefined** and **data** is the global HTTP proxy configuration. Otherwise, **error** is an error object.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 401     | Parameter error.             |
| 202     | Non-system applications use system APIs.             |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getGlobalHttpProxy((error: BusinessError, data: connection.HttpProxy) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## connection.getGlobalHttpProxy<sup>10+</sup>

getGlobalHttpProxy(): Promise\<HttpProxy>;

Obtains the global network proxy configuration information. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                             | Description                                 |
| --------------------------------- | ------------------------------------- |
| Promise\<[HttpProxy](js-apis-net-connection.md#httpproxy10)> | Promise used to return the result.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 202     | Non-system applications use system APIs.             |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getGlobalHttpProxy().then((data: connection.HttpProxy) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## connection.setGlobalHttpProxy<sup>10+</sup>

setGlobalHttpProxy(httpProxy: HttpProxy, callback: AsyncCallback\<void>): void

Sets the global network HTTP proxy configuration information. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description                                                        |
| --------- | ----------------------- | ---- | ------------------------------------------------------------ |
| httpProxy | [HttpProxy](js-apis-net-connection.md#httpproxy10) | Yes  | Global HTTP proxy configuration of the network.                                 |
| callback  | AsyncCallback\<void>    | Yes  | Callback used to return the result. If the global HTTP proxy configuration of the network is set successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 202     | Non-system applications use system APIs.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let exclusionStr = "192.168,baidu.com";
let exclusionArray = exclusionStr.split(',');
let httpProxy: connection.HttpProxy = {
    host: "192.168.xx.xxx",
    port: 8080,
    exclusionList: exclusionArray
}
connection.setGlobalHttpProxy(httpProxy, (err: BusinessError) => {
    if (err) {
        console.error(`setGlobalHttpProxy failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`setGlobalHttpProxy success.`);
});
```

## connection.setGlobalHttpProxy<sup>10+</sup>

setGlobalHttpProxy(httpProxy: HttpProxy): Promise\<void>;

Sets the global network HTTP proxy configuration information. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                                                        | Mandatory| Description            |
| --------- | ------------------------------------------------------------ | ---- | ---------------- |
| httpProxy | [HttpProxy](js-apis-net-connection.md#httpproxy10)                                      | Yes  | Global HTTP proxy configuration of the network.|

**Return value**

| Type                                       | Description                         |
| ------------------------------------------- | ----------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 401     | Parameter error.               |
| 202     | Non-system applications use system APIs.               |
| 2100001 | Invalid parameter value.                |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let exclusionStr = "192.168,baidu.com";
let exclusionArray = exclusionStr.split(',');
connection.setGlobalHttpProxy({
  host: "192.168.xx.xxx",
  port: 8080,
  exclusionList: exclusionArray
} as connection.HttpProxy).then(() => {
  console.info("success");
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```


## connection.enableAirplaneMode

enableAirplaneMode(callback: AsyncCallback\<void>): void

Enables the airplane mode. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                             | Mandatory| Description              |
| -------- | ------------------------------------------------- | ---- | ------------------ |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result.        |

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 202     | Non-system applications use system APIs.              |
| 401     | Parameter error.               |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.enableAirplaneMode((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## connection.enableAirplaneMode

enableAirplaneMode(): Promise\<void>

Enables airplane mode. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                                       | Description                         |
| ------------------------------------------- | ----------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 202     | Non-system applications use system APIs.              |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.enableAirplaneMode().then((error: void) => {
  console.error(JSON.stringify(error));
});
```

## connection.disableAirplaneMode

disableAirplaneMode(callback: AsyncCallback\<void>): void

Disables airplane mode. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                             | Mandatory| Description              |
| -------- | ------------------------------------------------- | ---- | ------------------ |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the airplane mode is disabled successfully, **error** is **undefined**. Otherwise, **error** is an error object.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 202     | Non-system applications use system APIs.              |
| 401     | Parameter error.               |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.disableAirplaneMode((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## connection.disableAirplaneMode

disableAirplaneMode(): Promise\<void>

Disables airplane mode. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                                       | Description                         |
| ------------------------------------------- | ----------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 202     | Non-system applications use system APIs.              |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.         |

**Example**

```ts
import { connection } from '@kit.NetworkKit';

connection.disableAirplaneMode().then((error: void) => {
  console.error(JSON.stringify(error));
});
```


## connection.factoryReset<sup>11+</sup>

factoryReset(): Promise\<void\>

Resets the network settings to the factory defaults. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                  | Description                   |
| ---------------------- | ----------------------- |
| Promise\<void\>        | Promise that returns no value. |

**Error codes**

| ID| Error Message                                   |
| ------- | ------------------------------------------  |
| 201     | Permission denied.                          |
| 202     | Non-system applications use system APIs.    |
| 2100002 | Failed to connect to the service.|
| 2100003 | System internal error.                      |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.factoryReset().then(() => {
    console.info("success");
}).catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
})
```

## ProxyMode<sup>20+</sup>

Enumerates the proxy modes. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name             | Value  | Description                    |
| -------------------- | ------ | ------------------------ |
| PROXY_MODE_OFF     | 0 | Proxy disabled.         |
| PROXY_MODE_AUTO    | 1 | Auto mode.         |

## connection.setProxyMode<sup>20+</sup>

setProxyMode(mode: ProxyMode): Promise\<void\>

Sets the proxy mode. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type            | Mandatory| Description              |
| ------ |----------------| ---- | ------------------ |
| mode   | [ProxyMode](#proxymode20) | Yes  | Specified proxy mode.  |

**Return value**

| Type| Description                    |
| -------- | ------------------------ |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
|-------|---------------|
| 201   | Permission denied.   |
| 202   | Non-system applications use system APIs. |



**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.setProxyMode(connection.ProxyMode.PROXY_MODE_AUTO).then(() => {
    console.info("Proxy mode set successfully.");
}).catch((error: BusinessError) => {
    console.error("Error setting proxy mode:", error);
});
```

## connection.getProxyMode<sup>20+</sup>

getProxyMode(): Promise\<ProxyMode\>

Obtains the current proxy mode. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                       | Description                         |
|---------------------------| ------------------------ |
| Promise\<[ProxyMode](#proxymode20)\> | Promise used to return the current proxy mode.|

**Error codes**

| ID| Error Message                       |
| ------- | -----------------------------  |
| 201     | Permission denied.             |
| 202     | Non-system applications use system APIs.              |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getProxyMode().then(mode => {
    console.info("Current proxy mode:", mode);
}).catch((error: BusinessError) => {
    console.error("Error getting proxy mode:", error);
});
```

## connection.createVlanInterface<sup>23+</sup>

createVlanInterface(ifName: string, vlanId: number): Promise\<void\>

Creates a virtual local area network (VLAN) with specified **vlanId** on a specified Ethernet NIC. This API uses a promise to return the result.

> **NOTE**
>
>- Currently, this API supports only the PC. For other device types, the error code 2100002 is returned when this API is called.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ---- | ----------------- |
| ifName | string | Yes| NIC name.|
| vlanId | number | Yes| VLAN ID. The value range is [0, 4094].|

**Return value**

| Type| Description|
| -------- | ------------------------ |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------- |
| 201 | Permission denied. |
| 202 | Nonsystem applications use system APIs. |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error. |
| 2100400 | The input network interface name is incorrect. |

**Example**

```typescript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
connection.createVlanInterface(ifName, vlanId).then(() => {
  console.info(`Create vlan success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to create vlan. Code:${error.code}, message:${error.message}`);
});
```

## connection.destroyVlanInterface<sup>23+</sup>

destroyVlanInterface(ifName: string, vlanId: number): Promise\<void\>

Deletes a VLAN specified by **vlanId** from a specified Ethernet NIC. This API uses a promise to return the result.

> **NOTE**
>
>- Currently, this API supports only the PC. For other device types, the error code 2100002 is returned when this API is called.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ---- | ----------------- |
| ifName | string | Yes| NIC name.|
| vlanId | number | Yes| VLAN ID. The value range is [0, 4094].|

**Return value**

| Type| Description|
| -------- | ------------------------ |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------- |
| 201 | Permission denied. |
| 202 | Nonsystem applications use system APIs. |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error. |
| 2100400 | The input network interface name is incorrect. |

**Example**

```typescript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
connection.destroyVlanInterface(ifName, vlanId).then(() => {
  console.info(`Destroy vlan success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to destroy vlan. Code:${error.code}, message:${error.message}`);
});
```

## connection.addVlanIp<sup>23+</sup>

addVlanIp(ifName: string, vlanId: number, address: LinkAddress): Promise\<void\>

Adds a specified IP address and subnet mask for the VLAN specified by **vlanId** on an Ethernet NIC. This API uses a promise to return the result.

> **NOTE**
>
>- Currently, this API supports only the PC. For other device types, the error code 2100002 is returned when this API is called.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ---- | ----------------- |
| ifName | string | Yes| NIC name.|
| vlanId | number | Yes| VLAN ID. The value range is [0, 4094].|
| address | [LinkAddress](js-apis-net-connection.md#linkaddress) | Yes| Network link information.|

**Return value**

| Type| Description|
| -------- | ------------------------ |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------- |
| 201 | Permission denied. |
| 202 | Nonsystem applications use system APIs. |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error. |
| 2100400 | The input network interface name is incorrect. |

**Example**

```typescript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
let netAddress: connection.NetAddress = {
  address: '192.168.1.1',
  family: 1,
  port: 8080
}
let address: connection.LinkAddress = {
  address: netAddress,
  prefixLength: 24
}
connection.addVlanIp(ifName, vlanId, address).then(() => {
  console.info(`Add vlan ip success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to add vlan ip. Code:${error.code}, message:${error.message}`);
});
```

## connection.deleteVlanIp<sup>23+</sup>

deleteVlanIp(ifName: string, vlanId: number, address: LinkAddress): Promise\<void\>

Deletes the configured IP address and subnet mask from the VLAN specified by **vlanId** on an Ethernet NIC. This API uses a promise to return the result.

> **NOTE**
>
>- Currently, this API supports only the PC. For other device types, the error code 2100002 is returned when this API is called.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ---- | ----------------- |
| ifName | string | Yes| NIC name.|
| vlanId | number | Yes| VLAN ID. The value range is [0, 4094].|
| address | [LinkAddress](js-apis-net-connection.md#linkaddress) | Yes| Network link information.|

**Return value**

| Type| Description|
| -------- | ------------------------ |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------- |
| 201 | Permission denied. |
| 202 | Nonsystem applications use system APIs. |
| 2100002 | Failed to connect to the service. |
| 2100003 | System internal error. |
| 2100400 | The input network interface name is incorrect. |
| 2100401 | The input IP address is not found. |

**Example**

```typescript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
let netAddress: connection.NetAddress = {
  address: '192.168.1.1',
  family: 1,
  port: 8080
}
let address: connection.LinkAddress = {
  address: netAddress,
  prefixLength: 24
}
connection.deleteVlanIp(ifName, vlanId, address).then(() => {
  console.info(`Delete vlan ip success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to delete vlan ip. Code:${error.code}, message:${error.message}`);
});
```