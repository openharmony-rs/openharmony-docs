# @ohos.bluetooth.access

Provides methods for enabling/disabling bluetooth or monitoring bluetooth state.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addPersistentDeviceId](arkts-connectivity-access-addpersistentdeviceid-f.md) | Add a persistent random device address. Once the randomized address is successfully added, the application can save it for an extended period of time. |
| [convertUuid](arkts-connectivity-access-convertuuid-f.md) | Convert 2-byte and 4-byte UUID strings to the 16-byte UUID string standard used in Bluetooth. |
| [deletePersistentDeviceId](arkts-connectivity-access-deletepersistentdeviceid-f.md) | Delete a persistent random device address. |
| [disableBluetooth](arkts-connectivity-access-disablebluetooth-f.md) | Disables Bluetooth on a device. |
| [disableBluetoothAsync](arkts-connectivity-access-disablebluetoothasync-f.md) | Asynchronous interface for disables Bluetooth on a device. |
| [enableBluetooth](arkts-connectivity-access-enablebluetooth-f.md) | Enables Bluetooth on a device. |
| [enableBluetoothAsync](arkts-connectivity-access-enablebluetoothasync-f.md) | Asynchronous interface for enables Bluetooth on a device. |
| [getPersistentDeviceIds](arkts-connectivity-access-getpersistentdeviceids-f.md) | Obtains the persistent randomized device address of the application. |
| [getState](arkts-connectivity-access-getstate-f.md) | Obtains the Bluetooth status of a device. |
| [isBluetoothSupported](arkts-connectivity-access-isbluetoothsupported-f.md) | Check whether Bluetooth is available. |
| [isValidRandomDeviceId](arkts-connectivity-access-isvalidrandomdeviceid-f.md) | Determine whether the randomized device address application can still be used. |
| [off](arkts-connectivity-access-off-f.md#offstatechange) | Unsubscribe the event reported when the Bluetooth state changes. |
| [on](arkts-connectivity-access-on-f.md#onstatechange) | Subscribe the event reported when the Bluetooth state changes. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [factoryReset](arkts-connectivity-access-factoryreset-f-sys.md) | Restoring bluetooth settings. |
| [factoryReset](arkts-connectivity-access-factoryreset-f-sys.md) | Restoring bluetooth settings. |
| [getLocalAddress](arkts-connectivity-access-getlocaladdress-f-sys.md) | Obtaining the MAC address of the local device. |
| [notifyDialogResult](arkts-connectivity-access-notifydialogresult-f-sys.md) | Notify bluetooth the result of bluetooth dialog. |
| [restrictBluetooth](arkts-connectivity-access-restrictbluetooth-f-sys.md) | Restrict Bluetooth BR/EDR ability on a device. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [NotifyDialogResultParams](arkts-connectivity-access-notifydialogresultparams-i-sys.md) | Describes the result of bluetooth dialog. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BluetoothState](arkts-connectivity-access-bluetoothstate-e.md) | The enum of bluetooth state. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DialogType](arkts-connectivity-access-dialogtype-e-sys.md) | The enum of bluetooth dialog type. |
<!--DelEnd-->
