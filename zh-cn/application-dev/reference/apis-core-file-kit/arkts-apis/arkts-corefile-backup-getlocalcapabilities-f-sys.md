# getLocalCapabilities（系统接口）

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## getLocalCapabilities

```TypeScript
function getLocalCapabilities(): Promise<FileData>
```

获取描述本地能力的JSON文件。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-backup-function getLocalCapabilities(): Promise<FileData>--><!--Device-backup-function getLocalCapabilities(): Promise<FileData>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FileData&gt; | Promise对象，返回包含本地能力文件描述符的FileData。返回的文件为临时文件，关闭后将自动删除。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

async function getLocalCapabilities() {
  try {
    let fileData = await backup.getLocalCapabilities();
    console.info('getLocalCapabilities success');
    console.info('fileData info:' + fileData.fd);
    fileIo.closeSync(fileData.fd);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

能力文件可以通过[@ohos.file.fs](js-apis-file-fs.md)提供的[fileIo.stat](js-apis-file-fs.md#fileiostat)等相关接口获取，能力文件内容示例：

```TypeScript
{
 "backupVersion" : "16.0",
 "bundleInfos" :[{
   "allToBackup" : true,
   "extensionName" : "BackupExtensionAbility",
   "name" : "com.example.hiworld",
   "needToInstall" : false,
   "spaceOccupied" : 0,
   "versionCode" : 1000000,
   "versionName" : "1.0.0"
   }],
 "deviceType" : "default",
 "systemFullName" : "OpenHarmony-4.0.0.0"
}

```


## getLocalCapabilities

```TypeScript
function getLocalCapabilities(callback: AsyncCallback<FileData>): void
```

获取描述本地能力的JSON文件。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-backup-function getLocalCapabilities(callback: AsyncCallback<FileData>): void--><!--Device-backup-function getLocalCapabilities(callback: AsyncCallback<FileData>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;FileData&gt; | 是 | 回调函数，返回包含本地能力文件描述符的FileData。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

try {
  backup.getLocalCapabilities((err: BusinessError, fileData: backup.FileData) => {
    if (err) {
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('getLocalCapabilities success');
    console.info('fileData info:' + fileData.fd);
    fileIo.closeSync(fileData.fd);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
}

```

能力文件可以通过[@ohos.file.fs](js-apis-file-fs.md)提供的[fileIo.stat](js-apis-file-fs.md#fileiostat)等相关接口获取，能力文件内容示例：

```TypeScript
{
 "backupVersion" : "16.0",
 "bundleInfos" :[{
   "allToBackup" : true,
   "extensionName" : "BackupExtensionAbility",
   "name" : "com.example.hiworld",
   "needToInstall" : false,
   "spaceOccupied" : 0,
   "versionCode" : 1000000,
   "versionName" : "1.0.0"
   }],
 "deviceType" : "default",
 "systemFullName" : "OpenHarmony-4.0.0.0"
}

```


## getLocalCapabilities

```TypeScript
function getLocalCapabilities(dataList: Array<IncrementalBackupTime>): Promise<FileData>
```

获取描述本地能力的JSON文件。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-backup-function getLocalCapabilities(dataList: Array<IncrementalBackupTime>): Promise<FileData>--><!--Device-backup-function getLocalCapabilities(dataList: Array<IncrementalBackupTime>): Promise<FileData>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataList | Array&lt;IncrementalBackupTime&gt; | 是 | 增量备份数据列表，包含待查询应用及其最后一次增量备份时间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FileData&gt; | Promise对象，返回包含本地能力文件描述符的FileData。返回的文件为临时文件，关闭后将自动删除。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

async function getLocalCapabilities() {
  try {
    let backupApps: backup.IncrementalBackupTime[] = [{
      bundleName: 'com.example.hiworld',
      lastIncrementalTime: 1700107870 // 调用者根据上次记录的增量备份时间
    }];
    let fileData = await backup.getLocalCapabilities(backupApps);
    console.info('getLocalCapabilities success');
    console.info('fileData info:' + fileData.fd);
    fileIo.closeSync(fileData.fd);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

