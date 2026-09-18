# updateTemplateFormDetailInfo (System API)

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## updateTemplateFormDetailInfo

```TypeScript
function updateTemplateFormDetailInfo(templateFormInfo: Array<formInfo.TemplateFormDetailInfo>): Promise<void>
```

Updates the static configuration information of a specified template widget on the current device. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templateFormInfo | Array&lt;[formInfo.TemplateFormDetailInfo](arkts-form-forminfo-templateformdetailinfo-i-sys.md)&gt; | Yes | Static configuration information of a specified template widget. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501013](../errorcode-form.md#16501013-operation-not-supported) | The system does not support the current operation. |
