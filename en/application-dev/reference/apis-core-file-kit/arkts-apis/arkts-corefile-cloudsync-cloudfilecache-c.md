# CloudFileCache

Provides APIs for the file manager application to download files from the Drive Kit to a local device.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## cleanAllFileCache

```TypeScript
cleanAllFileCache(): Promise<void>
```

Clean all downloaded files except those not yet migrated to the cloud or those that are being written to.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900010 | Try again. |

## cleanFileCache

```TypeScript
cleanFileCache(uri: string): void
```

Deletes a cache file. This API returns the result synchronously.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the cache file to delete. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.cleanFileCache(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("clean file cache failed with error message: " + err.message + ", error code: " + err.code);
}
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **CloudFileCache** instance. Data is not shared between multiple instances.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

## getCachedTotalSize

```TypeScript
getCachedTotalSize(): Promise<number>
```

Query the total size of cached files.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Return the total size of cached files. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900010 | Try again. |

## off

```TypeScript
off(event: 'progress', callback?: Callback<DownloadProgress>): void
```

Removes the specified callback from the device-cloud file cache progress.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'progress' | Yes | Event type. The value is **progress**, which indicates the sync progress event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md)&gt; | No | Callback used to return the file download progress. If this parameter is not specified, this API unregisters all callbacks for the download progress event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

## off

```TypeScript
off(event: 'batchDownload', callback?: Callback<MultiDownloadProgress>): void
```

Removes the listener added via the [on](#on-1) API for file batch downloads.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'batchDownload' | Yes | Event type. The value is **'batchDownload'**, indicating the batch download event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md)&gt; | No | Callback used to return the download progress of a file. If this parameter is set, the specified callback will be canceled; otherwise, all currently subscribed callbacks of the same event type will be canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## on

```TypeScript
on(event: 'progress', callback: Callback<DownloadProgress>): void
```

Registers a listener for the download progress of a file from the Drive Kit.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'progress' | Yes | Event. The value is **progress**, which indicates the download progress event of a cloud file. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md)&gt; | Yes | Callback used to return the file download progress. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

## on

```TypeScript
on(event: 'batchDownload', callback: Callback<MultiDownloadProgress>): void
```

Registers a listener for the batch download of a file from the Drive Kit.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'batchDownload' | Yes | Event type. The value is **'batchDownload'**, indicating the batch download event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md)&gt; | Yes | Callback used to return the download progress of a file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## start

```TypeScript
start(uri: string): Promise<void>
```

Starts downloading a file from the Drive Kit to the local device. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file to download. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |
| 14000002 | Invalid uri. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
  });
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}

fileCache.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.start(uri, (err: BusinessError) => {
  if (err) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});
```

## start

```TypeScript
start(uri: string, callback: AsyncCallback<void>): void
```

Starts downloading a file from the Drive Kit to the local device. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file to download. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to start downloading a cloud file asynchronously. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |
| 14000002 | Invalid uri. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
  });
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}

fileCache.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.start(uri, (err: BusinessError) => {
  if (err) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});
```

## startBatch

```TypeScript
startBatch(uris: Array<string>, fileType?: DownloadFileType): Promise<number>
```

Starts the batch download of a file from the Drive Kit. This API uses a promise to return the result.

Different batch download tasks can be distinguished by the task ID returned.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | Yes | URI list. A maximum of 400 URIs can be transferred at a time. An error (22400004) will be thrown if the number of URIs exceeds 400. |
| fileType | [DownloadFileType](arkts-corefile-cloudsync-downloadfiletype-e.md) | No | File type. The default value is **CONTENT**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the ID of the batch download task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid uri. |
| 22400004 | Exceed the maximum limit. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
try {
  fileCache.on('batchDownload', (pg: cloudSync.MultiDownloadProgress) => {
    console.info(`batch download state: ${pg.state}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}

let uriList: Array<string> = [];
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  console.info(`start batch download successfully, taskId: ${downloadId}`);
}).catch((err: BusinessError) => {
  console.error(`start download failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## stop

```TypeScript
stop(uri: string, needClean?: boolean): Promise<void>
```

Stops downloading a file from the Drive Kit to the local device. This API uses a promise to return the result.

When **stop()** is called, the current file download process terminates, and downloaded files are retained by default. You can call **start()** to resume the download.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file to download. |
| needClean | boolean | No | Whether to delete the downloaded files. The default value **false** means not to delete the downloaded files; the value **true** means the opposite.<br>This parameter is available since API version 12.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.stop(uri, true).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});
```

## stop

```TypeScript
stop(uri: string, callback: AsyncCallback<void>): void
```

Stops downloading a file from the Drive Kit to the local device. This API uses an asynchronous callback to return the result.

When **stop()** is called, the current file download process terminates, and downloaded files are retained. You can call **start()** to resume the download.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file to download. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to stop downloading a cloud file asynchronously. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.stop(uri, true).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});
```

## stopBatch

```TypeScript
stopBatch(downloadId: number, needClean?: boolean): Promise<void>
```

Stops the batch download task enabled by [startBatch](#startbatch) of a file from the Drive Kit. This API uses a promise to return the result.

When **stopBatch()** is called, the batch download terminates. The **needClean** parameter determines whether to delete incompletely downloaded files.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| downloadId | number | Yes | ID of the download task to be stopped. |
| needClean | boolean | No | Whether to delete incompletely downloaded files. The default value **false** means not to delete the files; the value **true** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let taskId = -1;
let uriList: Array<string> = [];
let fileCache = new cloudSync.CloudFileCache();
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  taskId = downloadId;
  console.info("start batch download successfully");
}).catch((err: BusinessError) => {
  console.error(`start batch download failed with error message: ${err.message}, error code: ${err.code}`);
});

let needStop = true;
if (needStop && taskId > 0) {
  fileCache.stopBatch(taskId, true).then(() => {
    console.info("stop batch download successfully");
  }).catch((err: BusinessError) => {
    console.error(`stop batch download failed with error message: ${err.message}, error code: ${err.code}`);
  });
}
```
