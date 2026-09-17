# getRemoteDeviceName

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getRemoteDeviceName

```TypeScript
function getRemoteDeviceName(deviceId: string): string
```

Obtains the name of a peer Bluetooth device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRemoteDeviceName](arkts-connectivity-bluetoothmanager-getremotedevicename-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | The address of the remote device. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the device name in character string format. |

**Examples**

```TypeScript
let remoteDeviceName : string = bluetooth.getRemoteDeviceName("XX:XX:XX:XX:XX:XX");
```
