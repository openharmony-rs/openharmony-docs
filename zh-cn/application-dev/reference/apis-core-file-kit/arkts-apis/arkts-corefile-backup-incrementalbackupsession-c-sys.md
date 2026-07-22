# IncrementalBackupSession（系统接口）

增量备份流程对象，用于支撑应用增量备份流程。

**起始版本：** 12

<!--Device-backup-class IncrementalBackupSession--><!--Device-backup-class IncrementalBackupSession-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## appendBundles

```TypeScript
appendBundles(bundlesToBackup: Array<IncrementalBackupData>): Promise<void>
```

添加需要增量备份的应用。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-appendBundles(bundlesToBackup: Array<IncrementalBackupData>): Promise<void>--><!--Device-IncrementalBackupSession-appendBundles(bundlesToBackup: Array<IncrementalBackupData>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundlesToBackup | Array&lt;IncrementalBackupData&gt; | 是 | 需要增量备份的应用数据列表。 |

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
| 13900011 | Out of memory |
| 13900025 | No space left on device |
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
let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程
let incrementalBackupData: backup.IncrementalBackupData = {
  bundleName: 'com.example.hiworld',
  lastIncrementalTime: 1700107870, // 调用者传递上一次备份的时间戳
  manifestFd: fileIo.openSync('/data/storage/el2/base/backup/manifest.json').fd // 调用者传递上一次备份的manifest文件句柄
}
let incrementalBackupDataArray: backup.IncrementalBackupData[] = [incrementalBackupData];
incrementalBackupSession.appendBundles(incrementalBackupDataArray).then(() => {
  console.info('appendBundles success');
}).catch((err: BusinessError) => {
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
}); // 添加需要增量备份的应用

```

## appendBundles

```TypeScript
appendBundles(bundlesToAppend: Array<IncrementalBackupData>, infos: string[]): Promise<void>
```

添加需要增量备份的应用。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-appendBundles(bundlesToAppend: Array<IncrementalBackupData>, infos: string[]): Promise<void>--><!--Device-IncrementalBackupSession-appendBundles(bundlesToAppend: Array<IncrementalBackupData>, infos: string[]): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundlesToAppend | Array&lt;IncrementalBackupData&gt; | 是 | 需要增量备份的应用数据列表。 |
| infos | string[] | 是 | 增量备份时各应用所需扩展信息的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. This error code is usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
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
let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程
let incrementalBackupData: backup.IncrementalBackupData = {
  bundleName: 'com.example.hiworld',
  lastIncrementalTime: 1700107870, // 调用者传递上一次备份的时间戳
  manifestFd: fileIo.openSync('/data/storage/el2/base/backup/manifest.json').fd // 调用者传递上一次备份的manifest文件句柄
}
    let infos: Array<string> = [
      `
      {
      "infos": [
          {
              "details": [
                  {
                      "detail": [
                          {
                              "key1": "value1",
                              "key2": "value2"
                          }
                      ]
                  }
              ],
              "type": "unicast",
              "bundleName": "com.example.hiworld"
          }
      ]
  },
  {
      "infos": [
          {
              "details": [
                  {
                      "detail": [
                          {
                              "key1": "value1",
                              "key2": "value2"
                          }
                      ]
                  }
              ],
              "type": "unicast",
              "bundleName": "com.example.myApp"
          }
      ]
  }
    `
  ]
let incrementalBackupDataArray: backup.IncrementalBackupData[] = [incrementalBackupData];
// 添加需要增量备份的应用
incrementalBackupSession.appendBundles(incrementalBackupDataArray, infos).then(() => {
  console.info('appendBundles success');
}).catch((err: BusinessError) => {
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
}); 

```

## cancel

```TypeScript
cancel(bundleName: string): number
```

取消指定应用的增量备份任务。

**起始版本：** 18

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-cancel(bundleName: string): int--><!--Device-IncrementalBackupSession-cancel(bundleName: string): int-End-->

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
      // 文件fd传输失败，调用取消接口，取消此应用的增量备份任务
      let result = incrementalBackupSession.cancel(err.name);
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
let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程
let backupBundles: Array<backup.IncrementalBackupData> = [];
let bundleData: backup.IncrementalBackupData = {
  bundleName: 'com.example.helloWorld',
  lastIncrementalTime: 1700107870, // 调用者传递上一次备份的时间戳
  manifestFd: fileIo.openSync('/data/storage/el2/base/backup/manifest.json').fd // 调用者传递上一次备份的manifest文件句柄
}
backupBundles.push(bundleData);
incrementalBackupSession.appendBundles(backupBundles).then(() => {
  console.info('appendBundles success');
}).catch((err: BusinessError) => {
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
});


```

## cleanBundleTempDir

```TypeScript
cleanBundleTempDir(bundleName: string): Promise<boolean>
```

清理指定应用的临时目录。

**起始版本：** 20

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-cleanBundleTempDir(bundleName: string): Promise<boolean>--><!--Device-IncrementalBackupSession-cleanBundleTempDir(bundleName: string): Promise<boolean>-End-->

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
    let res = await incrementalBackupSession.cleanBundleTempDir(bundleName);
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
let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程

```

## constructor

```TypeScript
constructor(callbacks: GeneralCallbacks)
```

构造IncrementalBackupSession实例。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-constructor(callbacks: GeneralCallbacks)--><!--Device-IncrementalBackupSession-constructor(callbacks: GeneralCallbacks)-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbacks | [GeneralCallbacks](arkts-corefile-backup-generalcallbacks-i-sys.md) | 是 | 备份流程所需的回调。 |

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
let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程

```

## getBackupDataSize

```TypeScript
getBackupDataSize(isPreciseScan: boolean, dataList: Array<IncrementalBackupTime>): Promise<void>
```

获取应用待备份数据量。

**起始版本：** 18

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-getBackupDataSize(isPreciseScan: boolean, dataList: Array<IncrementalBackupTime>): Promise<void>--><!--Device-IncrementalBackupSession-getBackupDataSize(isPreciseScan: boolean, dataList: Array<IncrementalBackupTime>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPreciseScan | boolean | 是 | 是否精确扫描，true表示精确扫描，false表示非精确扫描。 |
| dataList | Array&lt;IncrementalBackupTime&gt; | 是 | 备份应用列表及其最后一次增量备份时间。 |

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
| 13900020 | Invalid argument |
| 13900042 | Internal error |

**示例：**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface ScannedInfos { // 用于解析扫描结果
  scanned: [];
  scanning: string;
}

interface ScannedInfo { // 用于解析单个应用的扫描结果
  bundleName: string;
  dataSize: number;
  incDataSize: number;
}

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => { // 定义备份/恢复过程中的通用回调
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
  },
  // 回调函数与getBackupDataSize配套使用，返回已获取到应用的数据量大小和正在获取数据量的应用的包名。
  // generalCallbacks中的onBackupSizeReport每隔5秒（如果5秒内获取完则立即返回）返回一次扫描结果，直到dataList中所有的应用数据量全部返回。
  onBackupSizeReport: (OnBackupSizeReport) => {
    console.info('dataSizeCallback success');
    const jsonObj: ScannedInfos | null = JSON.parse(OnBackupSizeReport); // 解析返回的信息并打印
    if (jsonObj) {
      const infos: ScannedInfo [] = jsonObj.scanned;
      for (let i = 0; i < infos.length; i++) {
        console.info('name: ' + infos[i].bundleName);
        console.info('dataSize: ' + infos[i].dataSize);
        console.info('incDataSize: ' + infos[i].incDataSize);
      }
      const scanning: string = jsonObj.scanning;
      console.info('scanning: ' + scanning);
    }
  }
};

let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程

let backupApps: backup.IncrementalBackupTime[] = [{
  bundleName: 'com.example.hiworld',
  lastIncrementalTime: 1700107870 // 调用者根据上次记录的增量备份时间
}];
try {
  incrementalBackupSession.getBackupDataSize(true, backupApps); // 获取backupApps中指定应用的待备份的数据量大小，true表示使用精确扫描
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getBackupDataSize failed. Code: ${err.code}, message: ${err.message}`);
}

```

异步返回JSON串示例：

```TypeScript
{
 "scanned": [ // 本次扫描完成的应用，已返回结果的应用在下一次回调中不会再继续返回
     {
         "name": "com.example.hiworld", // 应用名称
         "dataSize": 1006060, // 数据量大小
         "incDataSize": 50800 // 增量数据量大小
     },
     {
         "name": "com.example.myAPP",
         "dataSize": 5000027,
         "incDataSize": 232344
     }
 ],
 "scanning" :"com.example.smartAPP" // 正在扫描的应用，在最后一次结果返回时，该字段为空
}

```

## getCompatibilityInfo

```TypeScript
getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>
```

获取指定应用的兼容性信息。

**起始版本：** 20

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>--><!--Device-IncrementalBackupSession-getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>-End-->

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

async function getIncBackupCompatibilityInfo() {
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程
  let bundleName = "com.example.helloWorld";
  let extInfo = ""; // 空表示无需给应用传额外信息
  try {
    let retInfo = await incrementalBackupSession.getCompatibilityInfo(bundleName, extInfo);
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

## getLocalCapabilities

```TypeScript
getLocalCapabilities(): Promise<FileData>
```

获取描述本地能力的JSON文件。

**起始版本：** 18

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-getLocalCapabilities(): Promise<FileData>--><!--Device-IncrementalBackupSession-getLocalCapabilities(): Promise<FileData>-End-->

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
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程
  let basePath = '/data/storage/el2/base/backup';
  let path = basePath + '/localCapabilities.json'; // 本地保存能力文件的路径
  try {
    let fileData = await incrementalBackupSession.getLocalCapabilities(); // 获取本地能力文件
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
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
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
    console.error(`parse failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

能力文件可以通过[@ohos.file.fs](js-apis-file-fs.md)提供的[fileIo.stat](js-apis-file-fs.md#fileiostat)等相关接口获取，能力文件内容示例：

```TypeScript
{
 "backupVersion" : "16.0",
 "bundleInfos" : [{
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

## release

```TypeScript
release(): Promise<void>
```

结束增量备份流程，断开应用与备份恢复服务的连接。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-IncrementalBackupSession-release(): Promise<void>--><!--Device-IncrementalBackupSession-release(): Promise<void>-End-->

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
let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // 创建增量备份流程
async function release() {
  try {
    await incrementalBackupSession.release(); // 结束增量备份流程
    console.info('release success');
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`release failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

