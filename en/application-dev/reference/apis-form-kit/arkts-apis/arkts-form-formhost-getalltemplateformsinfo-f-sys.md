# getAllTemplateFormsInfo (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## getAllTemplateFormsInfo

```TypeScript
function getAllTemplateFormsInfo(): Promise<Array<formInfo.FormInfo>>
```

Obtains the template widget information provided by all applications on the device. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-formHost-function getAllTemplateFormsInfo(): Promise<Array<formInfo.FormInfo>>--><!--Device-formHost-function getAllTemplateFormsInfo(): Promise<Array<formInfo.FormInfo>>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

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

<!--Del-->
**Examples**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.getAllTemplateFormsInfo().then((data: formInfo.FormInfo[]) => {
    for (let info of data) {
      console.info(`getAllTemplateFormsInfo bundleName: ${info.bundleName}, moduleName: ${info.moduleName}, name: ${info.name}`);
    }
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
