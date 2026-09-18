# getState

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): BluetoothState
```

Obtains the Bluetooth status of a device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getState](arkts-connectivity-bluetoothmanager-getstate-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetooth-bluetoothstate-e.md) | Returns the Bluetooth status, which can be [STATE_OFF](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_off), [STATE_TURNING_ON](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_turning_on), [STATE_ON](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_on), [STATE_TURNING_OFF](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_turning_off), [STATE_BLE_TURNING_ON](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_ble_turning_on), [STATE_BLE_ON](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_ble_on), or [STATE_BLE_TURNING_OFF](arkts-connectivity-bluetooth-bluetoothstate-e.md#state_ble_turning_off). |

**Examples**

```TypeScript
let state : bluetooth.BluetoothState = bluetooth.getState();
```
