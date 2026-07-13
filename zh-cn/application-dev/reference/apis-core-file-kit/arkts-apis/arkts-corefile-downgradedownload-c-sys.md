# DowngradeDownload（系统接口）

全量下载：为云盘管理应用提供集中下载云端数据的能力。

云盘全量下载对象，用于支撑云盘管理应用完成云盘文件的全量下载流程。

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(bundleName: string)
```

全量下载对象的构造函数，用于获取指定包名的DowngradeDownload类的实例。

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system applicationuses system API. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.demo.a';
try {
  let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to create downgrade manager object, error code: ${error.code}, message: ${error.message}`);
}

```

## getCloudFileInfo

```TypeScript
getCloudFileInfo(): Promise<CloudFileInfo>
```

获取需要全量下载的应用仅位于本地、仅位于云端或者本地和云端均有的文件大小和个数信息。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CloudFileInfo&gt; | Promise对象，返回携带本地与云端文件信息的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system applicationuses system API. |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900010 | Try again. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.getCloudFileInfo().then((fileInfo: cloudSyncManager.CloudFileInfo) => {
  console.info("cloud file info: " + JSON.stringify(fileInfo));
}).catch((err: BusinessError) => {
  console.error(`Failed to get downgrade info, error message: ${err.message}, error code: ${err.code}`);
});

```

## startDownload

```TypeScript
startDownload(callback: Callback<DownloadProgress>): Promise<void>
```

启动指定应用的云文件的全量下载，使用Promise异步回调。使用callback异步回调。

同一应用存在正在执行的全量下载任务的情况下，重复触发会返回错误信息（22400006）。

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;DownloadProgress&gt; | 是 | 回调函数。全量下载进度，参数为DownloadProgress，返回值为void。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system applicationuses system API. |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 22400006 | The same task is already in progress. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
let callback = (data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSyncManager.DownloadState.COMPLETED) {
    console.info('Downgrade finished.');
  } else if (data.state == cloudSyncManager.DownloadState.STOPPED) {
    console.info(`Downgrade stopped, reason: ${data.stopReason}.`);
  }
};
downgradeMgr.startDownload(callback).then(() => {
  console.info("Downgrade started successfully.");
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});

```

## startTransfer

```TypeScript
startTransfer(targetUri: string, callback: Callback<TransferProgress>): void
```

将云盘目录下已完成本地下载的文件搬迁至指定目录，过程中通过回调上报搬迁进度。使用callback异步回调。

同一应用存在正在执行的搬迁任务的情况下，重复触发会返回错误信息（22400006）。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetUri | string | 是 | 用于存放搬迁后的文件路径URI，必须以“/file://docs/storage/Users/currentUser/”为前缀。 |
| callback | Callback&lt;TransferProgress&gt; | 是 | 回调函数，返回搬迁进度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900001 | Operation not permitted. Possible causes:<br>1.The DowngradeDownload task is running.<br>2.The full data synchronization task is running. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified.<br>2.The length of the input uri does not meet the value range requirement.<br>3.The input uri does not belong to a File Manager public directory. |
| 22400006 | The same task is already in progress. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetPath: string = "file://docs/storage/Users/currentUser/Download/";
try {
    let downgradeMgr = new cloudSyncManager.DowngradeDownload("com.demo");
    downgradeMgr.startTransfer(targetPath, (data: cloudSyncManager.TransferProgress) => {
        console.info(`Transfer progress: successfulCount: ${data.successfulCount}, totalCount: ${data.totalCount}`);
    });
} catch (err) {
    let e = err as BusinessError;
    console.error(`transfer files failed with error message: ${e.message}, error code: ${e.code}`);
}

```

## stopDownload

```TypeScript
stopDownload(): Promise<void>
```

停止由[startDownload](arkts-corefile-downgradedownload-c-sys.md#startdownload-1)触发的全量下载任务，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system applicationuses system API. |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.startDownload((data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
}).then(() => {
  console.info("Downgrade started successfully.");
  let needStop = true;
  if (needStop) {
    downgradeMgr.stopDownload().then(() => {
      console.info("Downgrade stopped successfully.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to stop downgrade, error message: ${err.message}, error code: ${err.code}`);
    });
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});

```

