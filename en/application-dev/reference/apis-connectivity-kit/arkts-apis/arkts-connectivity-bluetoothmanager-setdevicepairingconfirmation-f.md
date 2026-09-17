# setDevicePairingConfirmation

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## setDevicePairingConfirmation

```TypeScript
function setDevicePairingConfirmation(device: string, accept: boolean): void
```

Sets the confirmation of pairing with a certain device. On API 10 and above, the permission required by this interface is changed from MANAGE_BLUETOOTH to ACCESS_BLUETOOTH and MANAGE_BLUETOOTH.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [setDevicePairingConfirmation](arkts-connectivity-connection-setdevicepairingconfirmation-f.md)

**Required permissions:** 
- API version 10 and later: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH
- API version 9: ohos.permission.MANAGE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | The address of the remote device. |
| accept | boolean | Yes | Indicates whether to accept the pairing request, `true` indicates accept or `false` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
// Subscribe to the pinRequired event and configure the pairing confirmation after receiving a pairing request from the remote device.
function onReceivePinRequiredEvent(data: bluetoothManager.PinRequiredParam) { // data is the input parameter for the pairing request.
    console.info('pin required  = '+ JSON.stringify(data));
    bluetoothManager.setDevicePairingConfirmation(data.deviceId, true);
}
try {
    bluetoothManager.on("pinRequired", onReceivePinRequiredEvent);
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```
