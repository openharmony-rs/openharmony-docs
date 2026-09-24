# getConnectionProperties

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getConnectionProperties

```TypeScript
function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback<ConnectionProperties>): void
```

Obtains the connection information of the data network specified by **NetHandle**, including the NIC name, domain name, link information, route information, network address, and maximum transmission unit. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ConnectionProperties](arkts-network-connection-connectionproperties-i.md)&gt; | Yes | Callback used to return the result. If the connection properties of the network specified by **netHandle** is obtained successfully, **error** is **undefined** and **data** is the obtained network connection information. Otherwise, **error** is an error object. |

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

// Example: Obtain the connection information of the default network.
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


<a id="getconnectionproperties-1"></a>

## getConnectionProperties

```TypeScript
function getConnectionProperties(netHandle: NetHandle): Promise<ConnectionProperties>
```

Obtains the connection information of the data network specified by **NetHandle**, including the NIC name, domain name, link information, route information, network address, and maximum transmission unit. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 8

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Handle of the data network. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ConnectionProperties](arkts-network-connection-connectionproperties-i.md)&gt; | Promise used to return the network connection information. |

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
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }

  connection.getConnectionProperties(netHandle).then((data: connection.ConnectionProperties) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  })
});
```
