# getSharedHosts (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## getSharedHosts

```TypeScript
function getSharedHosts(): Promise<SharedHost[]>
```

Get all available shared hosts.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SharedHost](arkts-basicservices-print-sharedhost-i.md)[]&gt; | Promise that resolves with the list of shared hosts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
