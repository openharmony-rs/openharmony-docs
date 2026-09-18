# updateSendRate (System API)

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## updateSendRate

```TypeScript
function updateSendRate(bundleName: string, sendRate: number): boolean
```

Update send file fd rate.

**Since:** 12

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | set update to bundleName app. |
| sendRate | number | Yes | set send file fd rate. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return update result, true is success, false is fail. |

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

function updateSendRate() {
  try {
    let bundleName = "com.example.myApp";
    let sendRate = 300;
    let result = backup.updateSendRate(bundleName, sendRate);
    if (result) {
      console.info('updateSendRate success');
    } else {
      console.info('updateSendRate fail');
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`updateSendRate failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```
