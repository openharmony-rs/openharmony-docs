# getBtConnectionState

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## getBtConnectionState

```TypeScript
function getBtConnectionState(): ProfileConnectionState
```

Get the local device connection state to any profile of any remote device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getProfileConnectionState](arkts-connectivity-connection-getprofileconnectionstate-f.md)

**Required permissions:** 
- API version 10 and later: ohos.permission.ACCESS_BLUETOOTH
- API version 9: ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md) | One of [STATE_DISCONNECTED](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md#state_disconnected), [STATE_CONNECTING](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md#state_connecting), [STATE_CONNECTED](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md#state_connected), [STATE_DISCONNECTING](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md#state_disconnecting). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
try {
    let connectionState: bluetoothManager.ProfileConnectionState = bluetoothManager.getBtConnectionState();
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```
