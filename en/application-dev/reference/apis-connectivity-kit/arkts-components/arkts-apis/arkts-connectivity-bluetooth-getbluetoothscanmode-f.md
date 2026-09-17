# getBluetoothScanMode

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getBluetoothScanMode

```TypeScript
function getBluetoothScanMode(): ScanMode
```

Obtains the Bluetooth scanning mode of a device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getBluetoothScanMode](arkts-connectivity-bluetoothmanager-getbluetoothscanmode-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ScanMode](arkts-connectivity-bluetooth-scanmode-e.md) | Returns the Bluetooth scanning mode, [ScanMode](arkts-connectivity-bluetooth-scanmode-e.md). |

**Examples**

```TypeScript
let scanMode : bluetooth.ScanMode = bluetooth.getBluetoothScanMode();
```
