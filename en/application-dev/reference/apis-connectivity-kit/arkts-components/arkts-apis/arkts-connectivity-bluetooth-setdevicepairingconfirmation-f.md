# setDevicePairingConfirmation

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## setDevicePairingConfirmation

```TypeScript
function setDevicePairingConfirmation(device: string, accept: boolean): boolean
```

Sets the confirmation of pairing with a certain device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDevicePairingConfirmation](arkts-connectivity-bluetoothmanager-setdevicepairingconfirmation-f.md)

**Required permissions:** ohos.permission.MANAGE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | The address of the remote device. |
| accept | boolean | Yes | Indicates whether to accept the pairing request, `true` indicates accept or `false` otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the pairing confirmation is set; returns `false` otherwise. |

**Examples**

```TypeScript
// Subscribe to the pinRequired event and configure the pairing confirmation after receiving a pairing request from the remote device.
function onReceivePinRequiredEvent(data : bluetooth.PinRequiredParam) { // data is the input parameter for the pairing request.
    console.info('pin required  = '+ JSON.stringify(data));
    bluetooth.setDevicePairingConfirmation(data.deviceId, true);
}
bluetooth.on("pinRequired", onReceivePinRequiredEvent);
```
