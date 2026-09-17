# fileSystemServiceRequest (System API)

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## fileSystemServiceRequest

```TypeScript
function fileSystemServiceRequest(config: FileSystemRequestConfig): Promise<number>
```

Requests filesystem garbage collection with specified configuration.

**Since:** 23

**Required permissions:** ohos.permission.BACKUP

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [FileSystemRequestConfig](arkts-corefile-backup-filesystemrequestconfig-i-sys.md) | Yes | Configuration parameters for garbage collection.<br>triggerType: 0. writeSize: 0 - 2097152(MB). waitTime: 0-300(s). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The errcode of garbage collection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13900020 | Invalid argument |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backup } from '@kit.CoreFileKit';

async function testFunction(size: number) {
  try {
    const result = await backup.fileSystemServiceRequest({
      triggerType: 0,
      writeSize: size,
      waitTime: 180
    });
    console.info(`fileSystemServiceRequest result: ${result}`);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`fileSystemServiceRequest err:` + err);
  }
}
```
