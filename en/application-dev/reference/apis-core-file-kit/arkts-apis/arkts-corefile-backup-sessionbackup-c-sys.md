# SessionBackup (System API)

Control class for backup procedure.

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## appendBundles

```TypeScript
appendBundles(bundlesToBackup: string[], infos?: string[]): Promise<void>
```

Append new bundles and backupInfos to backup.

**Since:** 12

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundlesToBackup | string[] | Yes | Bundles to backup. |
| infos | string[] | No | Infos to backup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
try {
  let backupApps: Array<string> = [
    "com.example.hiworld",
  ];
  sessionBackup.appendBundles(backupApps, (err: BusinessError) => {
    if (err) {
      console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('appendBundles success');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
}
```

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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
async function appendBundles() {
  try {
    let backupApps: Array<string> = [
      "com.example.hiworld",
      "com.example.myApp"
    ];
    await sessionBackup.appendBundles(backupApps);
    console.info('appendBundles success');
    // Application information is carried. In the following, infos, details, and type are fixed parameters.
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
    await sessionBackup.appendBundles(backupApps, infos);
    console.info('appendBundles success');
  } catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## appendBundles

```TypeScript
appendBundles(bundlesToBackup: string[], callback: AsyncCallback<void>): void
```

Append new bundles to backup.

**Since:** 10

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundlesToBackup | string[] | Yes | Bundles to backup. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Asynchronous callback to be called when appendBundles has finished. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
try {
  let backupApps: Array<string> = [
    "com.example.hiworld",
  ];
  sessionBackup.appendBundles(backupApps, (err: BusinessError) => {
    if (err) {
      console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('appendBundles success');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
}
```

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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
async function appendBundles() {
  try {
    let backupApps: Array<string> = [
      "com.example.hiworld",
      "com.example.myApp"
    ];
    await sessionBackup.appendBundles(backupApps);
    console.info('appendBundles success');
    // Application information is carried. In the following, infos, details, and type are fixed parameters.
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
    await sessionBackup.appendBundles(backupApps, infos);
    console.info('appendBundles success');
  } catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## cancel

```TypeScript
cancel(bundleName: string): number
```

cancel the application being backup.

**Since:** 18

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Set the bundleName of the application to be canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Return cancel result, 0 is success, 13500011 is fail, 13500012 is not have task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

let generalCallbacks: backup.GeneralCallbacks = {
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      // If the FD fails to be passed, call the cancel API to cancel the backup task of the application.
      let result = sessionBackup.cancel(err.name);
      console.info('cancel result:' + result);
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
let backupBundles: Array<string> = ["com.example.helloWorld"];
sessionBackup.appendBundles(backupBundles);
```

## cleanBundleTempDir

```TypeScript
cleanBundleTempDir(bundleName: string): Promise<boolean>
```

Provides an interface for the tool to clear temporary directories

**Since:** 20

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Set the bundleName of the application to be cleaned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Return clean result, true is success, false is fail. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |

**Examples**

```TypeScript
import { fileIo, backup} from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function cleanBundleTempDir(bundleName: string) {
  try {
    let res = await sessionBackup.cleanBundleTempDir(bundleName);
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

let generalCallbacks: backup.GeneralCallbacks = { // Define general callbacks to be used in the backup or restore process.
  // Callback when the file is sent successfully.
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onFileReady succeeded.`);
    fileIo.closeSync(file.fd);
  },
  // Callback when the application backup or restore starts.
  onBundleBegin: (err: BusinessError<string|void>, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleBegin succeeded.`);
  },
  // Callback when the application backup or restore is complete. cleanBundleTempDir is called for cleanup.
  onBundleEnd: (err: BusinessError<string|void>, bundleName: string) => {
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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
```

## constructor

```TypeScript
constructor(callbacks: GeneralCallbacks)
```

Constructor for obtaining the instance of the SessionBackup class.

**Since:** 10

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbacks | [GeneralCallbacks](arkts-corefile-backup-generalcallbacks-i-sys.md) | Yes | Callbacks to be registered for the backup. |

**Examples**

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
  onBundleBegin: (err: BusinessError<string|void>, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.data}`);
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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
```

## getBackupDataSize

```TypeScript
getBackupDataSize(isPreciseScan: boolean, dataList: Array<IncrementalBackupTime>): Promise<void>
```

Obtain application data size to be backed up.

**Since:** 18

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPreciseScan | boolean | Yes | Indicates whether to obtain the exact data size. |
| dataList | Array&lt;[IncrementalBackupTime](arkts-corefile-backup-incrementalbackuptime-i-sys.md)&gt; | Yes | Application list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Internal error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

interface scannedInfos { // Parse the scanning result.
  scanned: [];
  scanning: string;
}

interface ScannedInfo { // Parse the scanning result of an application.
  bundleName: string;
  dataSize: number;
  incDataSize: number;
}

let generalCallbacks: backup.GeneralCallbacks = { // Define general callbacks to be used in the backup or restore process.
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
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
  },
  onBackupSizeReport: (OnBackupSizeReport) => { // The callback function is used together with getBackupDataSize to return the obtained application data size and the bundle name of the application whose data size is being retrieved. onBackupSizeReport in generalCallbacks returns the scan result every 5 seconds, or immediately if the data retrieval process is completed within 5 seconds, until all application data in dataList is returned.
    console.info('dataSizeCallback success');
    const jsonObj: scannedInfos | null = JSON.parse(OnBackupSizeReport); // Parse and print the returned information.
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

let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
let backupApps: backup.IncrementalBackupTime[] = [{
  bundleName: "com.example.hiworld",
  lastIncrementalTime: 0 // The caller performs incremental backup based on the last recorded time. The value is 0 for full backup.
}];
try {
  sessionBackup.getBackupDataSize(false, backupApps); // Obtain the data to be backed up of a specified application in backupApps. The value false indicates that inaccurate scanning is used.
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getBackupDataSize failed. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
Example of a JSON string returned asynchronously:
```

## getCompatibilityInfo

```TypeScript
getCompatibilityInfo(bundleName: string, extInfo: string): Promise<string>
```

Provides an interface for the tool to get compatibility info.

**Since:** 20

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Set the bundleName of the application that need to get compatibilityInfo. |
| extInfo | string | Yes | Indicates the extension information of application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Return compatibility info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |

**Examples**

```TypeScript
import { fileIo, backup } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = { // Define general callbacks to be used in the backup or restore process.
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onFileReady succeeded.`);
    fileIo.closeSync(file.fd);
  },
  onBundleBegin: (err: BusinessError<string|void>, bundleName: string) => {
    if (err) {
      console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`onBundleBegin succeeded.`);
  },
  onBundleEnd: (err: BusinessError<string|void>, bundleName: string) => {
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

async function getBackupCompatibilityInfo() {
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
  let bundleName = "com.example.helloWorld";
  let extInfo = ""; // An empty string means no extra information needs to be passed to the application.
  try {
    let retInfo = await sessionBackup.getCompatibilityInfo(bundleName, extInfo);
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

Obtain a Json file that describes local capabilities.

**Since:** 18

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileData](arkts-corefile-backup-filedata-i-sys.md)&gt; | A FileData holding all the local capabilities. The returned file is a temporal file that will be deleted automatically when closed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900020 | Invalid argument |
| 13900042 | Internal error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

interface test { // Parse the capability file.
  bundleInfos: [];
  deviceType: string;
  systemFullName: string;
}

interface BundleInfo { // Obtain the local capability information of an application.
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
  extraInfo: object;
}

let generalCallbacks: backup.GeneralCallbacks = { // Define general callbacks to be used in the backup or restore process.
  onFileReady: (err: BusinessError, file: backup.File) => {
    if (err) {
      console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onFileReady success');
    fileIo.closeSync(file.fd);
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
async function getLocalCapabilitiesTest() {
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
  let basePath = '/data/storage/el2/base/backup'; 
  let path = basePath + '/localCapabilities.json'; // Local path for storing capability files.
  try {
    let fileData = await sessionBackup.getLocalCapabilities(); // Obtain the local capability file.
    if (fileData) {
      console.info('getLocalCapabilities success');
      console.info('fileData info:' + fileData.fd);
      if (!fileIo.accessSync(basePath)) {
        fileIo.mkdirSync(basePath);
        console.info('create success' + basePath);
      }
      fileIo.copyFileSync(fileData.fd, path); // Save the obtained local capability file to the local host.
      fileIo.closeSync(fileData.fd);
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
  }
  let data = fileIo.readTextSync(path, 'utf8'); // Obtain information from the local capability file.
  try {
    const jsonsObj: test | null = JSON.parse(data); // Parse the local capability file and print some information.
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
    console.error(`parse failed. message: ${error.message}`);
  }
}
```

```TypeScript
The capability file can be obtained by using fileIo.stat of the [@ohos.file.fs](arkts-corefile-fileio-n.md) module. The following is an example of the capability file.
```

## release

```TypeScript
release(): Promise<void>
```

End Backup process

**Since:** 12

**Required permissions:** ohos.permission.BACKUP

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

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
let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
sessionBackup.release(); // Release the backup session when the backup process is complete.
console.info('release success');
```
