# revokeSharedDirectoryPermission (System API)

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## revokeSharedDirectoryPermission

```TypeScript
function revokeSharedDirectoryPermission(): Promise<void>
```

Revokes permission for application-shared directories

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_SHARED_FILE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 13900001 | Operation not permitted. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeSharedDirectoryPermission() {
  try {
    fileShare.revokeSharedDirectoryPermission().then(() => {
      console.info('revokeSharedDirectoryPermission success');
    }).catch((err: BusinessError) => {
      console.error(`revokeSharedDirectoryPermission err: ${JSON.stringify(err)}`);
    });
  } catch (error) {
    console.error(`revokeSharedDirectoryPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```
