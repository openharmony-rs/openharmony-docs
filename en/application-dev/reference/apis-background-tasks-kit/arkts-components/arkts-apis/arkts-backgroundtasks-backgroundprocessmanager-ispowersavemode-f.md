# isPowerSaveMode

## Modules to Import

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## isPowerSaveMode

```TypeScript
function isPowerSaveMode(pid: number): Promise<boolean>
```

Queries whether the process is in power saving mode. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.BACKGROUND_MANAGER_POWER_SAVE_MODE

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pid | number | Yes | Process ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the query result. The value **true** means that the process is in power saving mode; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [31800002](../errorcode-backgroundProcessManager.md#31800002-invalid-parameter) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';

let pid = 33333;
try {
    backgroundProcessManager.isPowerSaveMode(pid).then((result: boolean) => {
        console.info("isPowerSaveMode: " + result.toString());
    });
} catch (error) {
    console.error(`isPowerSaveMode failed, errCode: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
