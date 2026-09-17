# isAppRunning

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## isAppRunning

```TypeScript
function isAppRunning(bundleName: string, appCloneIndex?: number): Promise<boolean>
```

Checks whether the application with the specified bundle name and application clone index is running across all users. This API uses a promise to return the result.

> **NOTE:** 
> 
> If the application is not installed for the current user, error code 16000073 is returned. If the application is
> installed for the current user, the system checks whether the application is running across all users.

**Since:** 14

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appCloneIndex | number | No | Index of an application clone. The value ranges from 0 to 1000. The value **0** means the main application, and a value greater than 0 means a specific application clone. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** is returned if at least one user is running the specified application. **false** is returned if none of the users are running the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  appManager.isAppRunning(bundleName).then((data: boolean) => {
      console.info(`data: ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`isAppRunning error, code: ${err.code}, msg:${err.message}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`isAppRunning error, code: ${code}, msg:${message}`);
}
```
