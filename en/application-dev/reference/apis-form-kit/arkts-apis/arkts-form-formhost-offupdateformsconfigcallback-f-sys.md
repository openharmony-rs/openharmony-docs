# offUpdateFormsConfigCallback (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## offUpdateFormsConfigCallback

```TypeScript
function offUpdateFormsConfigCallback(callback?: formInfo.UpdateFormsConfigCallback): void
```

Unregister the callback for updating form config.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [formInfo.UpdateFormsConfigCallback](arkts-form-forminfo-updateformsconfigcallback-t-sys.md) | No | Identifies the callback for updating form config. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |

**Examples**

```TypeScript
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.offUpdateFormsConfigCallback();
  console.info(`offUpdateFormsConfigCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
