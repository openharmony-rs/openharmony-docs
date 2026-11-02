# offGetVisibleFormRect (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## offGetVisibleFormRect

```TypeScript
function offGetVisibleFormRect(callback?: formInfo.GetFormRectInfoCallback): void
```

Meaning: deregistration to obtain the visible card area Application scenario: Callback of the area where the card is used to obtain the visible card is deregistered in the FMS. Effect: The FMS clears the callback record.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

<!--Device-formHost-function offGetVisibleFormRect(callback?: formInfo.GetFormRectInfoCallback): void--><!--Device-formHost-function offGetVisibleFormRect(callback?: formInfo.GetFormRectInfoCallback): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [formInfo.GetFormRectInfoCallback](arkts-form-forminfo-getformrectinfocallback-t-sys.md) | No | Callback function used by the widget host to process the request and return the position and dimension of the widget relative to the upper-left corner of the screen. The unit is vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
