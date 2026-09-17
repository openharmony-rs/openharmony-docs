# optimizeStorage (System API)

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## optimizeStorage

```TypeScript
function optimizeStorage():Promise<void>
```

Optimizes the resources that have been synced to the cloud from the local Gallery and executes the automatic aging policy according to the remaining local space. This API uses a promise to return the result.

**Since:** 17

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API.<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudSync.optimizeStorage().then(() => {
  console.info("optimize storage successfully");   // The foreground UX waits for blocking operations to complete.
}).catch((err: BusinessError) => {
  console.error("optimize storage failed with error message: " + err.message + ", error code: " + err.code);
});
```
