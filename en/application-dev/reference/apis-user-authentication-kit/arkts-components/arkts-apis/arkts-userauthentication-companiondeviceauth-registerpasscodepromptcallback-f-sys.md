# registerPasscodePromptCallback (System API)

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## registerPasscodePromptCallback

```TypeScript
function registerPasscodePromptCallback(callback: PasscodePromptCallback): void
```

Registers the callback invoked when the framework needs a companion device passcode. If a callback has already been registered, the new one replaces it.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [PasscodePromptCallback](arkts-userauthentication-companiondeviceauth-passcodepromptcallback-t-sys.md) | Yes | Callback invoked by the framework when a passcode is required. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |
