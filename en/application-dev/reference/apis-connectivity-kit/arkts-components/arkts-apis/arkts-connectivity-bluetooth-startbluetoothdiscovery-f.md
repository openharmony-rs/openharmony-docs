# startBluetoothDiscovery

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## startBluetoothDiscovery

```TypeScript
function startBluetoothDiscovery(): boolean
```

Starts scanning Bluetooth devices.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startBluetoothDiscovery](arkts-connectivity-bluetoothmanager-startbluetoothdiscovery-f.md)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH and ohos.permission.LOCATION

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the scan is started successfully; returns `false` otherwise. |

**Examples**

```TypeScript
let deviceId : Array<string>;
function onReceiveEvent(data : Array<string>) {
    deviceId = data;
}
bluetooth.on('bluetoothDeviceFind', onReceiveEvent);
let result : boolean = bluetooth.startBluetoothDiscovery();
```
