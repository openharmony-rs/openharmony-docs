# getNetExtAttributeSync

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getNetExtAttributeSync

```TypeScript
function getNetExtAttributeSync(netHandle: NetHandle): string
```

Obtains the extended attributes of the network specified by **netHandle** to determine its security level. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 20

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Extended network attributes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netHandle = connection.getDefaultNetSync();
if (netHandle.netId != 0) {
  let netExtAttribute: string = connection.getNetExtAttributeSync(netHandle);
  console.info("getNetExtAttribute: " + netExtAttribute);
}
```
