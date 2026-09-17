# clearUpAppData (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## clearUpAppData

```TypeScript
function clearUpAppData(bundleName: string, appCloneIndex?: number): Promise<void>
```

Clears data of a specified application based on the bundle name and application clone index. This API uses a promise to return the result.

**Since:** 13

**Required permissions:** ohos.permission.CLEAN_APPLICATION_DATA

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appCloneIndex | number | No | Index of the application clone. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = 'com.ohos.demo';
let appCloneIndex: number = 0;

try {
  appManager.clearUpAppData(bundleName, appCloneIndex).then(() => {
    console.info(`clearUpAppData success.`);
  }).catch((err: BusinessError) => {
    console.error(`clearUpAppData fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```
