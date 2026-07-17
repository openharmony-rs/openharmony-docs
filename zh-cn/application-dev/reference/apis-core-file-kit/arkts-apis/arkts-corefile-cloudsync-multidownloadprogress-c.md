# MultiDownloadProgress

云文件批量缓存的进度信息。

**起始版本：** 20

<!--Device-cloudSync-class MultiDownloadProgress--><!--Device-cloudSync-class MultiDownloadProgress-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## getFailedFiles

```TypeScript
getFailedFiles(): Array<FailedFileInfo>
```

获取批量缓存失败的文件列表。

**起始版本：** 20

<!--Device-MultiDownloadProgress-getFailedFiles(): Array<FailedFileInfo>--><!--Device-MultiDownloadProgress-getFailedFiles(): Array<FailedFileInfo>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<FailedFileInfo> | 返回缓存失败的文件URI列表及其对应的错误类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let taskId = -1;
let failedList: Array<cloudSync.FailedFileInfo> = [];
let fileCache = new cloudSync.CloudFileCache();
let callback = (data: cloudSync.MultiDownloadProgress) => {
  console.info(`Batch download progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSync.State.FAILED) {
    console.info(`Batch download stopped, error type: ${data.errType}.`);
    failedList = data.getFailedFiles();
  }
};

try {
  fileCache.on('batchDownload', callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to register download callback, error code: ${error.code}, message: ${error.message}`);
}

let uriList: Array<string> = [];
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  taskId = downloadId;
  console.info("start batch download successfully");
}).catch((err: BusinessError) => {
  console.error(`start batch download failed with error message: ${err.message}, error code: ${err.code}`);
});

```

## getSuccessfulFiles

```TypeScript
getSuccessfulFiles(): Array<string>
```

获取批量缓存成功的文件列表。

**起始版本：** 20

<!--Device-MultiDownloadProgress-getSuccessfulFiles(): Array<string>--><!--Device-MultiDownloadProgress-getSuccessfulFiles(): Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 数组类型，返回缓存成功的文件URI列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let finishedList: Array<string> = [];
let fileCache = new cloudSync.CloudFileCache();
let callback = (data: cloudSync.MultiDownloadProgress) => {
  console.info(`Batch download progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSync.State.COMPLETED) {
    console.info(`Batch download stopped, error type: ${data.errType}.`);
    finishedList = data.getSuccessfulFiles();
  }
};

try {
  fileCache.on('batchDownload', callback);
} catch (e) {
  const error = e as BusinessError;
  console.error(`Failed to register download callback, error code: ${error.code}, message: ${error.message}`);
}

let uriList: Array<string> = [];
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  console.info(`start batch download successfully, taskId: ${downloadId}`);
}).catch((err: BusinessError) => {
  console.error(`start batch download failed with error message: ${err.message}, error code: ${err.code}`);
});

```

## downloadedSize

```TypeScript
downloadedSize: number
```

已缓存的文件大小，取值范围为 [0, INT64_MAX)，单位：Byte。如果进度异常，返回值为 INT64_MAX。

**类型：** number

**起始版本：** 20

<!--Device-MultiDownloadProgress-downloadedSize: long--><!--Device-MultiDownloadProgress-downloadedSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## errType

```TypeScript
errType: DownloadErrorType
```

返回批量缓存任务执行失败时的错误类型。

**类型：** DownloadErrorType

**起始版本：** 20

<!--Device-MultiDownloadProgress-errType: DownloadErrorType--><!--Device-MultiDownloadProgress-errType: DownloadErrorType-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## failedCount

```TypeScript
failedCount: number
```

缓存失败的文件数，取值范围为0至400，单位：个。如果进度异常，返回值为-1。

**类型：** number

**起始版本：** 20

<!--Device-MultiDownloadProgress-failedCount: int--><!--Device-MultiDownloadProgress-failedCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## state

```TypeScript
state: State
```

批量缓存任务的执行状态。

**类型：** State

**起始版本：** 20

<!--Device-MultiDownloadProgress-state: State--><!--Device-MultiDownloadProgress-state: State-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## successfulCount

```TypeScript
successfulCount: number
```

缓存成功的文件数量，取值范围为0至400，单位：个。如果进度异常，返回值为-1。

**类型：** number

**起始版本：** 20

<!--Device-MultiDownloadProgress-successfulCount: int--><!--Device-MultiDownloadProgress-successfulCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## taskId

```TypeScript
taskId: number
```

批量缓存任务的ID，取值范围为0到INT64_MAX。如果进度异常，返回值为-1。

**类型：** number

**起始版本：** 20

<!--Device-MultiDownloadProgress-taskId: long--><!--Device-MultiDownloadProgress-taskId: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## totalCount

```TypeScript
totalCount: number
```

文件总数，取值范围为0至400，单位：个。如果进度异常，返回值为-1。

**类型：** number

**起始版本：** 20

<!--Device-MultiDownloadProgress-totalCount: int--><!--Device-MultiDownloadProgress-totalCount: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## totalSize

```TypeScript
totalSize: number
```

待缓存的文件总大小，取值范围为 [0, INT64_MAX)，单位为 Byte。如果进度异常，返回值为 INT64_MAX。

**类型：** number

**起始版本：** 20

<!--Device-MultiDownloadProgress-totalSize: long--><!--Device-MultiDownloadProgress-totalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

