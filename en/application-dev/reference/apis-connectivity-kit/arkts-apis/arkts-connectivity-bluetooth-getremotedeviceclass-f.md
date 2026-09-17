# getRemoteDeviceClass

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getRemoteDeviceClass

```TypeScript
function getRemoteDeviceClass(deviceId: string): DeviceClass
```

Obtains the class of a peer Bluetooth device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRemoteDeviceClass](arkts-connectivity-bluetoothmanager-getremotedeviceclass-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | The address of the remote device. |

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceClass](arkts-connectivity-bluetooth-deviceclass-i.md) | The class of the remote device, [DeviceClass](arkts-connectivity-bluetooth-deviceclass-i.md). |

**Examples**

```TypeScript
let remoteDeviceClass : bluetooth.DeviceClass = bluetooth.getRemoteDeviceClass("XX:XX:XX:XX:XX:XX");
```
