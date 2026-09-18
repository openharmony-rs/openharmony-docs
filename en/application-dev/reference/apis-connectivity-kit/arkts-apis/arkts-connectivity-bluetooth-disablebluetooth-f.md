# disableBluetooth

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## disableBluetooth

```TypeScript
function disableBluetooth(): boolean
```

Disables Bluetooth on a device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [disableBluetooth](arkts-connectivity-bluetoothmanager-disablebluetooth-f.md)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if Bluetooth is being disabled; returns `false` if an error occurs. |

**Examples**

```TypeScript
let disable : boolean = bluetooth.disableBluetooth();
```
