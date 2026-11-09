# killProcessWithAccountSafely (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## killProcessWithAccountSafely

```TypeScript
function killProcessWithAccountSafely(bundleName: string, accountId: number, clearPageStack: boolean, appIndex?: number):
    Promise<void>
```

Kills processes based on bundle name, account ID, appIndex safely. If the target process is protected, it cannot be terminated. This API uses a promise to return the result.

> **NOTE:** 
> 
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the
> current user.

**Since:** 26.1.0

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**Model restriction:** This API can be used only in the stage model.

<!--Device-appManager-function killProcessWithAccountSafely(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):    Promise<void>--><!--Device-appManager-function killProcessWithAccountSafely(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):    Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| accountId | number | Yes | ID of a system account. |
| clearPageStack | boolean | Yes | Whether to clear the page stack. **true** to clear, **false** otherwise. |
| appIndex | number | No | Index of an application clone. Default value is 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system server failed. |
| 16000210 | The target process is protected by an MDM application and cannot be terminated. |
