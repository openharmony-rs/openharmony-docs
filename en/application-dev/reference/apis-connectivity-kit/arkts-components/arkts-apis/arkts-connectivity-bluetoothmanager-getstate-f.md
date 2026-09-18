# getState

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): BluetoothState
```

Obtains the Bluetooth status of a device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getState](arkts-connectivity-access-getstate-f.md)

**Required permissions:** 
- API version 10 and later: ohos.permission.ACCESS_BLUETOOTH
- API version 9: ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md) | Returns the Bluetooth status, which can be [STATE_OFF](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_off), [STATE_TURNING_ON](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_turning_on), [STATE_ON](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_on), [STATE_TURNING_OFF](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_turning_off), [STATE_BLE_TURNING_ON](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_ble_turning_on), [STATE_BLE_ON](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_ble_on), or [STATE_BLE_TURNING_OFF](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md#state_ble_turning_off). |

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
    let state: bluetoothManager.BluetoothState = bluetoothManager.getState();
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```
