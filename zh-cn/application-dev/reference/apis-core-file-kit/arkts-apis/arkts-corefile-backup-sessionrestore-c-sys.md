# SessionRestore（系统接口）

恢复流程对象，用于支撑应用全量恢复流程。

**起始版本：** 10

<!--Device-backup-class SessionRestore--><!--Device-backup-class SessionRestore-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## appendBundles

```TypeScript
appendBundles(remoteCapabilitiesFd: number, bundlesToBackup: string[], infos?: string[]): Promise<void>
```

添加需要恢复的应用及其扩展信息。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-appendBundles(remoteCapabilitiesFd: int, bundlesToBackup: string[], infos?: string[]): Promise<void>--><!--Device-SessionRestore-appendBundles(remoteCapabilitiesFd: int, bundlesToBackup: string[], infos?: string[]): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| remoteCapabilitiesFd | number | 是 | 保存远端设备能力信息的已打开JSON文件描述符。 |
| bundlesToBackup | string[] | 是 | 需要恢复的应用名称数组。 |
| infos | string[] | 否 | 恢复时各应用所需扩展信息的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
async function appendBundles() {
  let fileData : backup.FileData = {
    fd : -1
  }
  try {
    fileData = await backup.getLocalCapabilities();
    console.info('getLocalCapabilities success');
    let restoreApps: Array<string> = [
      "com.example.hiworld",
    ];
    await sessionRestore.appendBundles(fileData.fd, restoreApps);
    console.info('appendBundles success');
    // 携带扩展参数的调用
    let infos: Array<string> = [
      `
       {
        "infos":[
          {
            "details": [
              {
                "detail": [
                  {
                    "source": "com.example.hiworld", // 应用旧系统包名
                    "target": "com.example.helloworld" // 应用新系统包名
                  }
                ],
                "type": "app_mapping_relation"
              }
            ],
            "type":"broadcast"
          }
        ]
       }
      `
    ]
    await sessionRestore.appendBundles(fileData.fd, restoreApps, infos);
    console.info('appendBundles success');
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
  } finally {
    fileIo.closeSync(fileData.fd);
  }
}

```

## appendBundles

```TypeScript
appendBundles(remoteCapabilitiesFd: number, bundlesToBackup: string[], callback: AsyncCallback<void>): void
```

添加需要恢复的应用。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-appendBundles(remoteCapabilitiesFd: int, bundlesToBackup: string[], callback: AsyncCallback<void>): void--><!--Device-SessionRestore-appendBundles(remoteCapabilitiesFd: int, bundlesToBackup: string[], callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| remoteCapabilitiesFd | number | 是 | 保存远端设备能力信息的已打开JSON文件描述符。 |
| bundlesToBackup | string[] | 是 | 需要恢复的应用名称数组。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 添加恢复应用完成后的异步回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
async function appendBundles() {
  let fileData : backup.FileData = {
    fd : -1
  }
  try {
    fileData = await backup.getLocalCapabilities();
    console.info('getLocalCapabilities success');
    let restoreApps: Array<string> = [
      "com.example.hiworld",
    ];
    sessionRestore.appendBundles(fileData.fd, restoreApps, (err: BusinessError) => {
      if (err) {
        console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('appendBundles success');
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
  } finally {
    fileIo.closeSync(fileData.fd);
  }
}

```

## cancel

```TypeScript
cancel(bundleName: string): number
```

取消指定应用的恢复任务。

**起始版本：** 18

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-cancel(bundleName: string): int--><!--Device-SessionRestore-cancel(bundleName: string): int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要取消任务的应用名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 取消结果，0表示成功，13500011表示失败，13500012表示没有对应任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      // 文件fd传输失败，调用取消接口，取消此应用的恢复任务
      let result = sessionRestore.cancel(file.bundleName);
      console.info('cancel result:' + result);
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
async function cancelTest() {
  let fileData: backup.FileData = {
    fd: -1
  }
  fileData = await backup.getLocalCapabilities(); // 备份恢复框架提供的getLocalCapabilities接口获取能力集文件。
  let backupBundles: Array<string> = ['com.example.helloWorld'];
  try {
    await sessionRestore.appendBundles(fileData.fd, backupBundles);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
  } finally {
    fileIo.closeSync(fileData.fd);
  }
}

```

## cleanBundleTempDir

```TypeScript
cleanBundleTempDir(bundleName: string): Promise<boolean>
```

清理指定应用的临时目录。

**起始版本：** 20

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-cleanBundleTempDir(bundleName: string): Promise<boolean>--><!--Device-SessionRestore-cleanBundleTempDir(bundleName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要清理临时目录的应用名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 清理结果，true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function cleanBundleTempDir(bundleName: string) {
  try {
    let res = await sessionRestore.cleanBundleTempDir(bundleName);
    if (res) {
      console.info(`cleanBundleTempDir succeeded.`);
    } else {
      console.info(`cleanBundleTempDir fail.`);
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`cleanBundleTempDir failed. Code: ${err.code}, message: ${err.message}`);
  }
}

let generalCallbacks: backup.GeneralCallbacks = { // 定义备份/恢复过程中的通用回调
  // 文件发送成功回调
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onFileReady succeeded.`);
    fileIo.closeSync(file.fd);
  },
  // 应用备份/恢复开始回调
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleBegin succeeded.`);
  },
  // 应用备份/恢复结束回调，在此处调用cleanBundleTempDir进行清理
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    cleanBundleTempDir(bundleName);
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onAllBundlesEnd success`);
  },
  onBackupServiceDied: () => {
    console.info(`service died`);
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程

```

## constructor

```TypeScript
constructor(callbacks: GeneralCallbacks)
```

构造SessionRestore实例。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-constructor(callbacks: GeneralCallbacks)--><!--Device-SessionRestore-constructor(callbacks: GeneralCallbacks)-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbacks | [GeneralCallbacks](arkts-corefile-backup-generalcallbacks-i-sys.md) | 是 | 恢复流程所需的回调。 |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程

```

## getApkFileHandle

```TypeScript
getApkFileHandle(path: string, fileName: string): Promise<FileData>
```

获取APK文件的文件句柄。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.BACKUP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SessionRestore-getApkFileHandle(path: string, fileName: string): Promise<FileData>--><!--Device-SessionRestore-getApkFileHandle(path: string, fileName: string): Promise<FileData>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | APK文件路径。 |
| fileName | string | 是 | APK文件名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FileData&gt; | Promise对象，返回包含APK文件描述符的FileData。返回的文件为临时文件，关闭后将自动删除。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |

**示例：**

```TypeScript
import { backup } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onFileReady succeeded.`);
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleBegin succeeded.`);
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleEnd succeeded.`);
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onAllBundlesEnd succeeded.`);
  },
  onBackupServiceDied: () => {
    console.info(`service died`);
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport succeeded, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess succeeded, bundleName: ${bundleName}, process: ${process}`);
  },
  onMigrateResult: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onMigrateResult failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onMigrateResult succeeded, bundleName: ' + bundleName);
  }
};

async function testGetApkFileHandle() {
  let sessionRestore = new backup.SessionRestore(generalCallbacks);
  try {
    let fileData: backup.FileData = await sessionRestore.getApkFileHandle("/data/storage/el1/base/files", "app.apk");
    console.info("getApkFileHandle succeeded, fd: " + fileData.fd);
    // 使用完毕后关闭文件描述符
    fileIo.closeSync(fileData.fd);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getApkFileHandle failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## getCompatibilityInfo

```TypeScript
getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>
```

获取指定应用的兼容性信息。

**起始版本：** 20

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>--><!--Device-SessionRestore-getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要获取兼容性信息的应用名称。 |
| extInfo | string | 是 | 传递给应用的额外信息，由应用自行处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回应用的兼容性信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |

**示例：**

```TypeScript
import { fileIo, backup } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = { // 定义备份/恢复过程中的通用回调
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onFileReady succeeded.`);
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleBegin succeeded.`);
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleEnd succeeded.`);
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onAllBundlesEnd success`);
  },
  onBackupServiceDied: () => {
    console.info(`service died`);
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};

async function getRestoreCompatibilityInfo() {
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
  let bundleName = "com.example.helloWorld";
  let extInfo = ""; // 空表示无需给应用传额外信息
  try {
    let retInfo = await sessionRestore.getCompatibilityInfo(bundleName, extInfo);
    if (retInfo) {
      console.info(`getCompatibilityInfo success ` + retInfo);
    } else {
      console.info(`bundle ` + bundleName + ' may not support getCompatibilityInfo');
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getCompatibilityInfo failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## getFileHandle

```TypeScript
getFileHandle(fileMeta: FileMeta): Promise<void>
```

向服务端请求共享文件，该接口属于零拷贝能力。开发者可通过onFileReady回调获取文件。客户端完成文件处理后，调用publishFile发布文件。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-getFileHandle(fileMeta: FileMeta): Promise<void>--><!--Device-SessionRestore-getFileHandle(fileMeta: FileMeta): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileMeta | [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 是 | 待发送文件的元数据。所有文件都应来自 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
async function getFileHandle() {
  try {
    let fileMeta: backup.FileMeta = {
      bundleName: 'com.example.hiworld',
      uri: "test.txt"
    }
    await sessionRestore.getFileHandle(fileMeta);
    console.info('getFileHandle success');
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getFileHandle failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## getFileHandle

```TypeScript
getFileHandle(fileMeta: FileMeta, callback: AsyncCallback<void>): void
```

向服务端请求共享文件，该接口属于零拷贝能力。开发者可通过onFileReady回调获取文件。客户端完成文件处理后，调用publishFile发布文件。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-getFileHandle(fileMeta: FileMeta, callback: AsyncCallback<void>): void--><!--Device-SessionRestore-getFileHandle(fileMeta: FileMeta, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileMeta | [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 是 | 待发送文件的元数据。所有文件都应来自 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 获取文件句柄完成后的异步回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
let fileMeta: backup.FileMeta = {
  bundleName: 'com.example.hiworld',
  uri: "test.txt"
}
sessionRestore.getFileHandle(fileMeta, (err: BusinessError) => {
  if (err) {
    console.error(`getFileHandle failed. Code: ${err.code}, message: ${err.message}`);
  }
  console.info('getFileHandle success');
});

```

## getFileHandles

```TypeScript
getFileHandles(fileMeta: FileMeta): Promise<void>
```

向服务端批量请求共享文件，该接口属于零拷贝能力。开发者可通过onFileReadyBatch回调获取文件。客户端完成文件处理后，调用publishFile发布文件。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.BACKUP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SessionRestore-getFileHandles(fileMeta: FileMeta): Promise<void>--><!--Device-SessionRestore-getFileHandles(fileMeta: FileMeta): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileMeta | [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 是 | 待发送文件的元数据。所有文件都应来自备份流程或getLocalCapabilities方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |

**示例：**

```TypeScript
import { fileIo, backup } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onFileReadyBatch: (error: BusinessError<void>, files: Array<backup.File>): void => {
    if (error) {
      console.error(`onFileReadyBatch failed. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let file of files) {
      console.info(`onFileReadyBatch success with file: ${file.bundleName}, ${file.uri}`);
      fileIo.closeSync(file.fd);
    }
  },
  onBundleBegin: (err: BusinessError<string|void>, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError<string|void>, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
// 创建恢复流程实例。
let sessionRestore = new backup.SessionRestore(generalCallbacks);
async function getFileHandles() {
  let testArray: string[] = ["test1", "test2"];
  try {
    let fileMeta: backup.FileMeta = {
      bundleName: "com.example.hiworld",
      uri: "test.txt",
      uris: testArray
    };
    await sessionRestore.getFileHandles(fileMeta);
    console.info('getFileHandles success');
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getFileHandles failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## getLocalCapabilities

```TypeScript
getLocalCapabilities(): Promise<FileData>
```

获取描述本地能力的JSON文件。

**起始版本：** 18

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-getLocalCapabilities(): Promise<FileData>--><!--Device-SessionRestore-getLocalCapabilities(): Promise<FileData>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FileData&gt; | Promise对象，返回包含本地能力文件描述符的FileData。返回的文件为临时文件，关闭后将自动删除。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Internal error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

interface LocalCapabilities { // 用于解析能力文件
  bundleInfos: BundleInfo[];
  deviceType: string;
  systemFullName: string;
}

interface BundleInfo { // 用于获取单个应用的本地能力信息
  name: string;
  appIndex: number;
  versionCode: number;
  versionName: string;
  spaceOccupied: number;
  allToBackup: boolean;
  increSpaceOccupied?: number;
  fullBackupOnly: boolean;
  extensionName: string;
  restoreDeps: string;
  supportScene: string;
  extraInfo: Record<string, Object>;
}

let generalCallbacks: backup.GeneralCallbacks = { // 定义备份/恢复过程中的通用回调
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleBegin success');
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onBundleEnd success');
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onAllBundlesEnd success');
  },
  onBackupServiceDied: () => {
    console.info('service died');
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
  }
};
async function getLocalCapabilitiesTest() {
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
  let basePath = '/data/storage/el2/base/backup';
  let path = basePath + '/localCapabilities.json'; // 本地保存能力文件的路径
  try {
    let fileData = await sessionRestore.getLocalCapabilities(); // 获取本地能力文件
    if (fileData) {
      console.info('getLocalCapabilities success');
      console.info('fileData info:' + fileData.fd);
      if (!fileIo.accessSync(basePath)) {
        fileIo.mkdirSync(basePath);
        console.info('create success' + basePath);
      }
      fileIo.copyFileSync(fileData.fd, path); // 将获取的本地能力文件保存到本地
      fileIo.closeSync(fileData.fd);
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed with code: ${err.code}, message: ${err.message}`);
  }
  let data = fileIo.readTextSync(path, 'utf8'); // 从本地的能力文件中获取信息
  try {
    const jsonsObj: LocalCapabilities | null = JSON.parse(data); // 解析本地的能力文件并打印部分信息
    if (jsonsObj) {
      const infos:BundleInfo [] = jsonsObj.bundleInfos;
      for (let i = 0; i < infos.length; i++) {
        console.info('name: ' + infos[i].name);
        console.info('appIndex: ' + infos[i].appIndex);
        console.info('allToBackup: ' + infos[i].allToBackup);
      }
      const systemFullName: string = jsonsObj.systemFullName;
      console.info('systemFullName: ' + systemFullName);
      const deviceType: string = jsonsObj.deviceType;
      console.info('deviceType: ' + deviceType);
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`parse failed with code: ${err.code}, message: ${err.message}`);
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

## migrateFile

```TypeScript
migrateFile(pathInfo: PathInfo, fileMeta: FileMeta): Promise<void>
```

将文件从源路径迁移到目标路径。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.BACKUP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SessionRestore-migrateFile(pathInfo: PathInfo, fileMeta: FileMeta): Promise<void>--><!--Device-SessionRestore-migrateFile(pathInfo: PathInfo, fileMeta: FileMeta): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfo | [PathInfo](arkts-corefile-backup-pathinfo-i-sys.md) | 是 | 包含源路径和目标路径的迁移路径信息。 |
| fileMeta | [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 是 | 包含应用名称及可选文件名的文件元数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |

**示例：**

```TypeScript
import { backup } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onFileReady succeeded.`);
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleBegin succeeded.`);
  },
  onBundleEnd: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleEnd succeeded.`);
  },
  onAllBundlesEnd: (err: BusinessError) => {
    if (err) {
      console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onAllBundlesEnd succeeded.`);
  },
  onBackupServiceDied: () => {
    console.info(`service died.`);
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport succeeded, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess succeeded, bundleName: ${bundleName}, process: ${process}`);
  },
  onMigrateResult: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onMigrateResult failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onMigrateResult succeeded, bundleName: ' + bundleName);
  }
};

async function testMigrateFile() {
  let sessionRestore = new backup.SessionRestore(generalCallbacks);
  try {
    await sessionRestore.migrateFile(
      {
        srcPath: "/data/storage/el1/base/files/",
        destPath: "/data/storage/el2/base/files/"
      },
      {
        bundleName: 'com.example.app',
        uri: "" // 按目录迁移文件时，将uri置为空
      }
    );
    console.info("migrateFile succeeded.");
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`migrateFile failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## publishFile

```TypeScript
publishFile(fileMeta: FileMeta): Promise<void>
```

向备份服务发布文件句柄，通知服务端文件内容已准备完成。该接口属于零拷贝能力。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-publishFile(fileMeta: FileMeta): Promise<void>--><!--Device-SessionRestore-publishFile(fileMeta: FileMeta): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileMeta | [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 是 | 待发送文件的元数据。应确保备份框架已持有 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let g_session: backup.SessionRestore;
let initMap = new Map<string, number>();
let testFileNum = 123; // 123: 恢复所需文件个数示例
let testBundleName = 'com.example.myapplication'; // 测试包名
initMap.set(testBundleName, testFileNum);
let countMap = new Map<string, number>();
countMap.set(testBundleName, 0); // 实际写入文件个数初始化
async function publishFile(file: backup.FileMeta) {
  let fileMeta: backup.FileMeta = {
    bundleName: file.bundleName,
    uri: ''
  }
  await g_session.publishFile(fileMeta);
}
function createSessionRestore() {
  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onFileReady success');
      fileIo.closeSync(file.fd);
      let cnt = countMap.get(file.bundleName) || 0;
      countMap.set(file.bundleName, cnt + 1); // 实际写入文件个数更新
      // 恢复所需文件个数与实际写入文件个数相等时调用，保证数据的一致性和完整性
      if (countMap.get(file.bundleName) == initMap.get(file.bundleName)) { // 每个包的所有文件收到后触发publishFile
        publishFile(file);
      }
      console.info('publishFile success');
    },
    onBundleBegin: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onBundleBegin success');
    },
    onBundleEnd: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onBundleEnd success');
    },
    onAllBundlesEnd: (err: BusinessError) => {
      if (err) {
        console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onAllBundlesEnd success');
    },
    onBackupServiceDied: () => {
      console.info('service died');
    },
    onResultReport: (bundleName: string, result: string) => {
      console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
    },
    onProcess: (bundleName: string, process: string) => {
      console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
    }
  };
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
  return sessionRestore;
}
g_session = createSessionRestore();

```

## publishFile

```TypeScript
publishFile(fileMeta: FileMeta, callback: AsyncCallback<void>): void
```

向备份服务发布文件句柄，通知服务端文件内容已准备完成。该接口属于零拷贝能力。

**起始版本：** 10

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-publishFile(fileMeta: FileMeta, callback: AsyncCallback<void>): void--><!--Device-SessionRestore-publishFile(fileMeta: FileMeta, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileMeta | [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 是 | 待发送文件的元数据。应确保备份框架已持有 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 发布文件句柄完成后的异步回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let g_session: backup.SessionRestore;
let initMap = new Map<string, number>();
let testFileNum = 123; // 123: 恢复所需文件个数示例
let testBundleName = 'com.example.myapplication'; // 测试包名
initMap.set(testBundleName, testFileNum);
let countMap = new Map<string, number>();
countMap.set(testBundleName, 0); // 实际写入文件个数初始化
function createSessionRestore() {
  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onFileReady success');
      fileIo.closeSync(file.fd);
      let cnt = countMap.get(file.bundleName) || 0;
      countMap.set(file.bundleName, cnt + 1); // 实际写入文件个数更新
      // 恢复所需文件个数与实际写入文件个数相等时调用，保证数据的一致性和完整性
      if (countMap.get(file.bundleName) == initMap.get(file.bundleName)) { // 每个包的所有文件收到后触发publishFile
        let fileMeta: backup.FileMeta = {
          bundleName: file.bundleName,
          uri: ''
        }
        g_session.publishFile(fileMeta, (err: BusinessError) => {
          if (err) {
            console.error(`publishFile failed. Code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('publishFile success');
        });
      }
    },
    onBundleBegin: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onBundleBegin success');
    },
    onBundleEnd: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onBundleEnd success');
    },
    onAllBundlesEnd: (err: BusinessError) => {
      if (err) {
        console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onAllBundlesEnd success');
    },
    onBackupServiceDied: () => {
      console.info('service died');
    },
    onResultReport: (bundleName: string, result: string) => {
      console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
    },
    onProcess: (bundleName: string, process: string) => {
     console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
    }
  };
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
  return sessionRestore;
}
g_session = createSessionRestore();

```

## release

```TypeScript
release(): Promise<void>
```

结束恢复流程，断开应用与备份恢复服务的连接。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-SessionRestore-release(): Promise<void>--><!--Device-SessionRestore-release(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let g_session: backup.SessionRestore;
let initMap = new Map<string, number>();
let testFileNum = 123; // 123: 恢复所需文件个数示例
let testBundleName = 'com.example.myapplication'; // 测试包名
initMap.set(testBundleName, testFileNum);
let countMap = new Map<string, number>();
countMap.set(testBundleName, 0); // 实际写入文件个数初始化
function createSessionRestore() {
  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onFileReady success');
      fileIo.closeSync(file.fd);
      let cnt = countMap.get(file.bundleName) || 0;
      countMap.set(file.bundleName, cnt + 1); // 实际写入文件个数更新
      // 恢复所需文件个数与实际写入文件个数相等时调用，保证数据的一致性和完整性
      if (countMap.get(file.bundleName) == initMap.get(file.bundleName)) { // 每个包的所有文件收到后触发publishFile
        let fileMeta: backup.FileMeta = {
          bundleName: file.bundleName,
          uri: ''
        }
        g_session.publishFile(fileMeta, (err: BusinessError) => {
          if (err) {
            console.error(`publishFile failed. Code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('publishFile success');
        });
      }
    },
    onBundleBegin: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onBundleBegin success');
    },
    onBundleEnd: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onBundleEnd success');
    },
    onAllBundlesEnd: (err: BusinessError) => {
      if (err) {
        console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('onAllBundlesEnd success');
    },
    onBackupServiceDied: () => {
      console.info('service died');
    },
    onResultReport: (bundleName: string, result: string) => {
      console.info(`onResultReport success, bundleName: ${bundleName}, result: ${result}`);
    },
    onProcess: (bundleName: string, process: string) => {
      console.info(`onProcess success, bundleName: ${bundleName}, process: ${process}`);
    }
  };
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // 创建恢复流程
  return sessionRestore;
}
g_session = createSessionRestore();
async function releaseSession() {
  try {
    await g_session.release();
    console.info('release success');
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`release failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

