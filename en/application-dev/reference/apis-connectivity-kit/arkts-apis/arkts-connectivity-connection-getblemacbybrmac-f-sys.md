# getBleMacByBrMac (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getBleMacByBrMac

```TypeScript
function getBleMacByBrMac(brMac: string): string
```

Obtains the real BLE address of a paired remote device based on its real BR address.

This API is used to identify the BR entry and the BLE entry of the same dual-mode device in the paired device list. The input brMac is the real BR address of a paired remote device, and the return value is the real BLE address of the same remote device.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

<!--Device-connection-function getBleMacByBrMac(brMac: string): string--><!--Device-connection-function getBleMacByBrMac(brMac: string): string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brMac | string | Yes | Indicates the real BR address of the paired remote device. For example,"11:22:33:AA:BB:FF". |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the real BLE address of the remote device. For example, "11:22:33:AA:BB:FF". |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900003 | Bluetooth disabled. |
| [2900016](../errorcode-bluetoothManager.md#2900016-device-not-paired) | Device unpaired. |
| 2900017 | No BLE address is associated with the input BR address. |
| 2900099 | Operation failed. |
