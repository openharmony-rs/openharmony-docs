# setNetExtAttributeSync

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setNetExtAttributeSync

```TypeScript
function setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void
```

Sets extended attributes of the network specified by **netHandle** to indicate its security level. This API returns the result synchronously.

> **NOTE:** 
> 
> Currently, this API is available only for PCs.

**Since:** 20

**Required permissions:** ohos.permission.SET_NET_EXT_ATTRIBUTE

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | Yes | Network handle. |
| netExtAttribute | string | Yes | Extended network attributes. |

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

let netExtAttribute: string = "xxx";
let netHandle = connection.getDefaultNetSync();
if (netHandle.netId != 0) {
  connection.setNetExtAttributeSync(netHandle, netExtAttribute);
}
```
