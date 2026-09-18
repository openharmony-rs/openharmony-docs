# getBackupInfo (System API)

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## getBackupInfo

```TypeScript
function getBackupInfo(bundleToBackup: string): string
```

Get Backup information from bundle.

**Since:** 12

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleToBackup | string | Yes | Bundle to backup. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return the backup application's info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backup } from '@kit.CoreFileKit';

function getBackupInfo() {
  try {
    let backupApp = "com.example.hiworld";
    let result = backup.getBackupInfo(backupApp);
    console.info('getBackupInfo success, result: ' + result);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getBackupInfo failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```
