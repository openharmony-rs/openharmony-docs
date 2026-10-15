# unregisterFormHostService (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## unregisterFormHostService

```TypeScript
function unregisterFormHostService(serviceId: string): Promise<void>
```

Unregister the form host service info.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

<!--Device-formHost-function unregisterFormHostService(serviceId: string): Promise<void>--><!--Device-formHost-function unregisterFormHostService(serviceId: string): Promise<void>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceId | string | Yes | Identifies service Id of the form host service. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501019](../errorcode-form.md#16501019-unable-to-unregister-the-widget-service-not-registered-by-the-current-application) | A form service not owned by you cannot be unregistered. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |

<!--Del-->
**Examples**

```TypeScript
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let serviceId: string = 'serviceId'; // ID of the service to be deregistered. Replace it with the actual service ID.
try {
  formHost.unregisterFormHostService(serviceId).then(() => {
    console.info('formHost unregisterFormHostService success');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
