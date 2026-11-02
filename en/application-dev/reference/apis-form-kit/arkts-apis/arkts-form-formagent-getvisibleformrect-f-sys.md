# getVisibleFormRect (System API)

## Modules to Import

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## getVisibleFormRect

```TypeScript
function getVisibleFormRect(formId: string): Promise<formInfo.Rect>
```

Obtains the visible position and dimension of a widget. This API uses a promise to return the result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-formAgent-function getVisibleFormRect(formId: string): Promise<formInfo.Rect>--><!--Device-formAgent-function getVisibleFormRect(formId: string): Promise<formInfo.Rect>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.Rect](arkts-form-forminfo-rect-i.md)&gt; | Promise used to return the position and dimension of the widget relative to the upper-left corner of the screen, in vp. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501001](../errorcode-form.md#16501001-widget-id-not-exist) | The ID of the form to be operated does not exist. |
| [16501003](../errorcode-form.md#16501003-widget-not-operatable) | The form cannot be operated by the current application. |
