# getTemplateFormsInfo (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## getTemplateFormsInfo

```TypeScript
function getTemplateFormsInfo(bundleName: string, moduleName?: string): Promise<Array<formInfo.FormInfo>>
```

Obtains the template widget information provided by a specified application on the device. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| moduleName | string | No | Module name. By default, no value is passed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[formInfo.FormInfo](arkts-form-forminfo-forminfo-i.md)&gt;&gt; | Promise used to return the information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
