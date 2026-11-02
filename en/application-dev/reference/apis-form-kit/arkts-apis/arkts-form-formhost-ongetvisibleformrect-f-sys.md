# onGetVisibleFormRect (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## onGetVisibleFormRect

```TypeScript
function onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void
```

Subscribes to the event of requesting visible widget position and dimension. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

<!--Device-formHost-function onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void--><!--Device-formHost-function onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [formInfo.GetFormRectInfoCallback](arkts-form-forminfo-getformrectinfocallback-t-sys.md) | Yes | Callback function used by the widget host to process the request and return the position and dimension of the widget relative to the upper-left corner of the screen. The unit is vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
