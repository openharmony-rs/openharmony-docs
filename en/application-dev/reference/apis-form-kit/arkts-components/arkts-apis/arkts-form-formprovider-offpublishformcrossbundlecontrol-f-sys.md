# offPublishFormCrossBundleControl (System API)

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## offPublishFormCrossBundleControl

```TypeScript
function offPublishFormCrossBundleControl(callback?: formInfo.PublishFormCrossBundleControlCallback): void
```

Unsubscribes from controls on cross-bundle widget addition to the home screen. This API uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.PUBLISH_FORM_CROSS_BUNDLE_CONTROL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [formInfo.PublishFormCrossBundleControlCallback](arkts-form-forminfo-publishformcrossbundlecontrolcallback-t-sys.md) | No | Callback function used to return the control result on cross-bundle widget addition to the home screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
