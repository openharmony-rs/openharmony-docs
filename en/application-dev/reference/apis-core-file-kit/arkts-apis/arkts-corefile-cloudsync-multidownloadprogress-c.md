# MultiDownloadProgress

Represents the batch download progress of a file from the Drive Kit.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## getFailedFiles

```TypeScript
getFailedFiles(): Array<FailedFileInfo>
```

Obtains the list of files that fail to be downloaded in batches.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[FailedFileInfo](arkts-corefile-cloudsync-failedfileinfo-i.md)&gt; | List of file URIs that fail to be downloaded and the corresponding error types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

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

Obtains the list of files that are successfully downloaded in batches.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of URIs of the files that are successfully downloaded. The value is an array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

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

Size of the downloaded file, in bytes. The value range is [0, INT64_MAX). If the progress is abnormal, the value **INT64_MAX** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## errType

```TypeScript
errType: DownloadErrorType
```

Type of the error returned when the batch download fails.

**Type:** [DownloadErrorType](arkts-corefile-cloudsync-downloaderrortype-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## failedCount

```TypeScript
failedCount: number
```

Number of files that fail to be downloaded. The value ranges from 0 to 400. If the progress is abnormal, the value **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## state

```TypeScript
state: State
```

Execution state of the batch download.

**Type:** [State](arkts-corefile-cloudsync-state-e.md)

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## successfulCount

```TypeScript
successfulCount: number
```

Number of successfully downloaded files. The value ranges from 0 to 400. If the progress is abnormal, the value **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## taskId

```TypeScript
taskId: number
```

ID of a batch download task. The value ranges from 0 to INT64_MAX. If the progress is abnormal, the value **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## totalCount

```TypeScript
totalCount: number
```

Total number of files. The value ranges from 0 to 400. If the progress is abnormal, the value **-1** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## totalSize

```TypeScript
totalSize: number
```

Total size of the files to be downloaded, in bytes. The value range is [0, INT64_MAX). If the progress is abnormal, the value **INT64_MAX** is returned.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core
