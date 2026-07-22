# getBackupInfo（系统接口）

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## getBackupInfo

```TypeScript
function getBackupInfo(bundleToBackup: string): string
```

获取需要备份的应用信息。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-backup-function getBackupInfo(bundleToBackup: string): string--><!--Device-backup-function getBackupInfo(bundleToBackup: string): string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleToBackup | string | 是 | 需要备份的应用名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回应用上报的备份信息，具体内容和格式由应用自定义。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backup } from '@kit.CoreFileKit';

function getBackupInfo() {
  try {
    let backupApp = 'com.example.hiworld';
    let result = backup.getBackupInfo(backupApp);
    console.info('getBackupInfo success, result: ' + result);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getBackupInfo failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

