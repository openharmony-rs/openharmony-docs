# getState

## Modules to Import

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): BluetoothState
```

Obtains the Bluetooth status of a device.

**Since:** 10

**Required permissions:** 
- API version 13 and later: N/A
- API versions 10 to 12: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [BluetoothState](arkts-connectivity-access-bluetoothstate-e.md) | Returns the Bluetooth status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 - 12 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let state = access.getState();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
