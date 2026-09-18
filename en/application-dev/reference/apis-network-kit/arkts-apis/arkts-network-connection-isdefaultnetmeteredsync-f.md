# isDefaultNetMeteredSync

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## isDefaultNetMeteredSync

```TypeScript
function isDefaultNetMeteredSync(): boolean
```

Checks whether the data traffic over the current network is metered. For example, data traffic over Wi-Fi is not metered, whereas that over cellular networks is. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 10

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value indicating whether data traffic over the current network is metered. The value **true** indicates that the data traffic is metered, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let isMetered = connection.isDefaultNetMeteredSync();
```
