# stopBluetoothDiscovery

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## stopBluetoothDiscovery

```TypeScript
function stopBluetoothDiscovery(): boolean
```

Stops Bluetooth device scanning.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stopBluetoothDiscovery](arkts-connectivity-bluetoothmanager-stopbluetoothdiscovery-f.md)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if scanning is stopped successfully; returns `false` otherwise. |

**Examples**

```TypeScript
let result : boolean = bluetooth.stopBluetoothDiscovery();
```
