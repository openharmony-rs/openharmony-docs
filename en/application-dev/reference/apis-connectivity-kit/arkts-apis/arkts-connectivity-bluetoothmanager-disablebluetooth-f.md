# disableBluetooth

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## disableBluetooth

```TypeScript
function disableBluetooth(): void
```

Disables Bluetooth on a device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [disableBluetooth](arkts-connectivity-access-disablebluetooth-f.md)

**Required permissions:** 
- API version 10 and later: ohos.permission.ACCESS_BLUETOOTH
- API version 9: ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
try {
    bluetoothManager.disableBluetooth();
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ", errMessage:" + (err as BusinessError).message);
}
```
