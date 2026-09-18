# pairDevice

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## pairDevice

```TypeScript
function pairDevice(deviceId: string): boolean
```

Starts pairing with a remote Bluetooth device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [pairDevice](arkts-connectivity-bluetoothmanager-pairdevice-f.md)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | The address of the remote device to pair. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the pairing process is started; returns `false` otherwise. |

**Examples**

```TypeScript
// The address can be scanned.
let result : boolean = bluetooth.pairDevice("XX:XX:XX:XX:XX:XX");
```
