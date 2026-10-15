# registerDeviceSelectCallback (System API)

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## registerDeviceSelectCallback

```TypeScript
function registerDeviceSelectCallback(callback: DeviceSelectCallback): void
```

Registers a callback for companion device selection. When the system requires the user to select a companion device, this callback is triggered. The application needs to return the information about the selected device in the callback. Through this callback, the application can implement custom device selection logic, for example, displaying a device selection screen for the user to select a device.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

<!--Device-companionDeviceAuth-function registerDeviceSelectCallback(callback: DeviceSelectCallback): void--><!--Device-companionDeviceAuth-function registerDeviceSelectCallback(callback: DeviceSelectCallback): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [DeviceSelectCallback](arkts-userauthentication-companiondeviceauth-deviceselectcallback-t-sys.md) | Yes | Callback for the companion device selection. When this callback is invoked, **selectPurpose** is passed in. The application needs to return the corresponding **DeviceSelectResult**, including the information about the selected device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |
