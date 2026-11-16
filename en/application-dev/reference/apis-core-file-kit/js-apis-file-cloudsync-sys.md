# @ohos.file.cloudSync (Device-Cloud Sync) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @reminder2352-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=cc1b47676eee26de6dfb56618584b714fd3922f9 translatedAt=2026-11-04T04:07:24.412Z pushedAt=2026-11-04T10:12:33.458Z nl=1 -->

The **cloudSync** module provides the device-cloud sync capabilities for applications. You can use the APIs to start or stop device-cloud sync and start or stop the download of images.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.file.cloudSync (Device-Cloud Sync Capability)](js-apis-file-cloudsync.md).

## Modules to Import

```ts
import { cloudSync } from '@kit.CoreFileKit';
```

## GallerySync

Provides APIs to implement device-cloud sync of media assets in **Gallery**. Before using the APIs of **GallerySync**, you need to create a **GallerySync** instance.

### constructor

constructor()

A constructor used to create a **GallerySync** instance.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Example**

```ts
let gallerySync = new cloudSync.GallerySync()
```

### on('progress')

on(evt: 'progress', callback: (pg: SyncProgress) => void): void

Registers a listener for the device-cloud sync progress.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| evt | string | Yes  | Event type. The value is **progress**, which indicates the sync progress event.|
| callback | (pg: SyncProgress) => void | Yes  | Callback used to return the sync progress. The input parameter is [SyncProgress](./js-apis-file-cloudsync.md#syncprogress12), and the return value is **void**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |

**Example**

```ts
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});
```

### off('progress')

off(evt: 'progress', callback: (pg: SyncProgress) => void): void

Removes the specified callback from the device-cloud sync progress.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| evt | string | Yes  | Event type. The value is **progress**, which indicates the sync progress event.|
| callback | (pg: SyncProgress) => void | Yes  | Callback used to return the sync progress. The input parameter is [SyncProgress](./js-apis-file-cloudsync.md#syncprogress12), and the return value is **void**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |

**Example**

```ts
let gallerySync = new cloudSync.GallerySync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("gallery sync state: " + pg.state + "error type: " + pg.error);
}

gallerySync.on('progress', callback);

gallerySync.off('progress', callback);
```

### off('progress')

off(evt: 'progress'): void

Removes all callbacks from the device-cloud sync progress.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| evt | string | Yes  | Event type. The value is **progress**, which indicates the sync progress event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |

**Example**

```ts
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
    console.info("syncState: " + pg.state);
});

gallerySync.off('progress');
```

### start

start(): Promise&lt;void&gt;

Starts device-cloud sync. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes:Incorrect parameter types. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003  | Low battery level. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});

gallerySync.start().then(() => {
  console.info("start sync successfully");
}).catch((err: BusinessError) => {
  console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
});
```

### start

start(callback: AsyncCallback&lt;void&gt;): void

Starts device-cloud sync. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to start device-cloud sync.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 22400001 | Cloud status not ready. |
| 22400002 | Network unavailable. |
| 22400003  | Low battery level. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.start((err: BusinessError) => {
  if (err) {
    console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start sync successfully");
  }
});
```

### stop

stop(): Promise&lt;void&gt;

Stops device-cloud sync. This API uses a promise to return the result.

> **NOTE**
>
> Calling **stop** will stop the sync process. To resume the sync, call [start](#start).

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes:Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop().then(() => {
  console.info("stop sync successfully");
}).catch((err: BusinessError) => {
  console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
});
```

### stop

stop(callback: AsyncCallback&lt;void&gt;): void

Stops device-cloud sync. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Calling **stop** will stop the sync process. To resume the sync, call [start](#start).

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to stop device-cloud sync.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop((err: BusinessError) => {
  if (err) {
    console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop sync successfully");
  }
});
```

## Download

Provides APIs for downloading image files to **Gallery**. Before using the APIs of **Download**, you need to create a **Download** instance.

### constructor

constructor()

A constructor used to create a **Download** instance.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Example**

```ts
let download = new cloudSync.Download()
```

### on('progress')

on(evt: 'progress', callback: (pg: DownloadProgress) => void): void

Registers a listener for the download progress of a cloud file.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| evt | string | Yes  | Event. The value is **progress**, which indicates the download progress event of a cloud file.|
| callback | (pg: DownloadProgress) => void | Yes  | Callback used to return the file download progress. The input parameter is [DownloadProgress](js-apis-file-cloudsync.md#downloadprogress11), and the return value is **void**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |

**Example**

```ts
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});
```

### off('progress')

off(evt: 'progress', callback: (pg: DownloadProgress) => void): void

Removes the specified callback from the device-cloud download progress.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| evt | string | Yes | Event type to unsubscribe from. The value is 'progress' (download process event). |
| callback | (pg: DownloadProgress) => void | Yes  | Callback used to return the file download progress. The input parameter is [DownloadProgress](js-apis-file-cloudsync.md#downloadprogress11), and the return value is **void**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |

**Example**

```ts
let download = new cloudSync.Download();

let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
}

download.on('progress', callback);

download.off('progress', callback);
```

### off('progress')

off(evt: 'progress'): void

Removes all callbacks from the device-cloud download progress.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| evt | string | Yes  | Event type. The value is **progress**, which indicates the download progress event of a cloud file.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |

**Example**

```ts
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
});

download.off('progress');
```

### start

start(uri: string): Promise&lt;void&gt;

Starts downloading a cloud file. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | string | Yes  | URI of the target file.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});

download.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});
```

### start

start(uri: string, callback: AsyncCallback&lt;void&gt;): void

Starts downloading a cloud file. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | string | Yes  | URI of the target file.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to start downloading a cloud file.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.start(uri, (err: BusinessError) => {
  if (err) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});
```

### stop

stop(uri: string): Promise&lt;void&gt;

Stops downloading a cloud file. This API uses a promise to return the result.

> **NOTE**
>
> Calling **stop** will terminate the download of the current file and clear the cache file. You can use **start** to start the download again.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | string | Yes  | URI of the target file.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});
```

### stop

stop(uri: string, callback: AsyncCallback&lt;void&gt;): void

Stops downloading a cloud file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Calling **stop** will terminate the download of the current file and clear the cache file. You can use **start** to start the download again.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | string | Yes  | URI of the target file.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to stop downloading a cloud file.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});
```

## FileSync<sup>12+</sup>

Provides APIs for the file manager application to perform device-cloud sync of the files stored in the Drive Kit. Before using the APIs of this class, you need to create a **FileSync** instance.

### constructor<sup>12+</sup>

constructor(bundleName: string)

A constructor used to create a **FileSync** instance.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| bundleName | string | Yes  | Bundle name.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
let fileSync = new cloudSync.FileSync("com.ohos.demo")
```

### registerUploadProgress

registerUploadProgress(callback: Callback&lt;UploadProgress&gt;): void

Registers a callback to listen for file upload progress changes. This API uses an asynchronous callback.

**Since:** 26.0.0

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ---- |
| callback | Callback&lt;[UploadProgress](#uploadprogress)&gt; | Yes | Callback function that listens for file upload progress changes. It is triggered when the file upload progress changes and returns the upload progress information. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes: 1.Mandatory parameters are left unspecified. 2.The number of instances registered at the same time exceeds the upper limit.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");

try {
  fileSync.registerUploadProgress((progress: cloudSync.UploadProgress) => {
    console.info("upload progress - uri: " + progress.uri + ", state: " + progress.state);
    console.info("processed: " + progress.processed + ", size: " + progress.size);
    console.info("error: " + progress.error);
  });
  console.info("register upload progress successfully");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("register upload progress failed with error message: " + error.message + ", error code: " + error.code);
}
```

### unregisterUploadProgress

unregisterUploadProgress(): void

Unregisters the upload progress callback function.

**Since:** 26.0.0

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900010 | Try again. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");

try {
  fileSync.unregisterUploadProgress();
  console.info("unregister upload progress successfully");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("unregister upload progress failed with error message: " + error.message + ", error code: " + error.code);
}
```

### getUploadList

getUploadList(uris: Array&lt;string&gt;): Promise&lt;Array&lt;UploadProgress&gt;&gt;

Obtains the file upload list and progress information. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name     | Type   | Mandatory | Description |
| ---------- | ------ | ---- | ---- |
| uris |  Array&lt;string&gt; | Yes   | Array of URIs of the files whose upload progress is to be queried. The array length ranges from 1 to 100. |

**Return value**

| Type                  | Description             |
| --------------------- | ---------------- |
| Promise&lt;Array&lt;[UploadProgress](#uploadprogress)&gt;&gt; | Promise object that returns the array of upload progress information.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900010  | Try again. |
| 13900020  | Invalid argument. Possible causes: 1.Mandatory parameters are left unspecified. 2.The length of the input parameter exceeds the upper limit. 3.The input parameter contains an invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");
let uris: string[] = ["file:///data/storage/el2/cloud/1.txt", "file:///data/storage/el2/cloud/2.jpg"];

fileSync.getUploadList(uris).then((progressList: Array<cloudSync.UploadProgress>) => {
  console.info("get upload list successfully, count: " + progressList.length);
  progressList.forEach((item) => {
    console.info("file uri: " + item.uri + ", state: " + item.state);
  })
}).catch((error: BusinessError) => {
  console.error("get upload list failed with error message: " + error.message + ", error code: " + error.code);
});
```

### pauseUpload

pauseUpload(uri: string): void

Pauses cloud file upload.

**Since:** 26.0.0

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ---- |
| uri | string | Yes | URI of the file to be paused. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 14000002 | Invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileSync.pauseUpload(uri);
  console.info("pause upload successfully.");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("pause upload failed with error message: " + error.message + ", error code: " + error.code);
}
```

### resumeUpload

resumeUpload(uri: string): void

Resumes the cloud file upload.

**Since:** 26.0.0

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ---- |
| uri | string | Yes | URI of the file whose upload is to be resumed. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 14000002 | Invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileSync.resumeUpload(uri);
  console.info("resume upload successfully.");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("resume upload failed with error message: " + error.message + ", error code: " + error.code);
}
```

## CloudFileCache<sup>11+</sup>

Provides APIs for the file manager application to download files from the Drive Kit to a local device.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

### constructor

constructor(bundleName: string)

Constructor of the End-to-Cloud Synchronization flow, used to obtain an instance of the CloudFileCache class.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ---- |
| bundleName | string | Yes | Package name of the application. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 202 | The caller is not a system application. |

**Example**

```ts
let fileCache = new cloudSync.CloudFileCache("com.ohos.demo");
```

### cleanCache<sup>11+</sup>

cleanCache(uri: string): void

Deletes a cache file. This API returns the result synchronously.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | string | Yes  | URI of the cache file to delete.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |
| 13900002  | No such file or directory. |
| 14000002  | Invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache("com.ohos.demo");
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.cleanCache(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("clean cache failed with error message: " + err.message + ", error code: " + err.code);
} 

```

### getDownloadList

getDownloadList(uris: Array&lt;string&gt;): Promise&lt;Array&lt;DownloadProgress&gt;&gt;

Gets the file download progress list. Uses a Promise for the async callback.

**Since:** 26.0.0

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ---- |
| uris | Array&lt;string&gt; | Yes | Array of file URIs whose download progress is to be queried. The array length ranges from 1 to 100. |

**Return value**

| Type | Description |
| --------------------- | ---------------- |
| Promise&lt;Array&lt;[DownloadProgress](js-apis-file-cloudsync.md#downloadprogress11)&gt;&gt; | Promise object that returns the list of file download progress results. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                     | Error Message        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900010  | Try again. |
| 13900020  | Invalid argument. Possible causes: 1.Mandatory parameters are left unspecified. 2.The length of the input parameter exceeds the upper limit. 3.The input parameter contains an invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache("com.ohos.demo");
let path1 = "/data/storage/el2/cloud/1.txt";
let path2 = "/data/storage/el2/cloud/2.txt";
let uri1 = fileUri.getUriFromPath(path1);
let uri2 = fileUri.getUriFromPath(path2);
let uriArray = [uri1, uri2];

try {
  fileCache.getDownloadList(uriArray).then((downloadList: Array<cloudSync.DownloadProgress>) => {
    console.info("get download list successfully");
    downloadList.forEach((item) => {
      console.info("download progress - uri: ".concat(item.uri, ", state: ").concat(item.state.toString()));
      console.info("processed: ".concat(item.processed.toString(), ", size: ").concat(item.size.toString()));
      console.info("error: ".concat(item.error.toString()));
    })
  }).catch((error: BusinessError) => {
    console.error("get download list failed with error message: " + error.message + ", error code: " + error.code);
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("get download list failed with error message: " + error.message + ", error code: " + error.code);
}
```
## cloudSync.getFileSyncState<sup>11+</sup>

getFileSyncState(uri: Array&lt;string&gt;): Promise&lt;Array&lt;FileSyncState&gt;&gt;

Obtains the file sync state. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | Array&lt;string&gt; | Yes  | URI of the file whose sync state is to be obtained.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;Array&lt;FileSyncState&gt;&gt; | Promise used to return the sync state obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |
| 13900002  | No such file or directory. |
| 14000002  | Invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let uris: Array<string> = ["file://uri"];
cloudSync.getFileSyncState(uris).then((syncStates: Array<cloudSync.FileSyncState>) => {
  syncStates.forEach((item) => {
    console.info("get file sync state successfully" + item);
  })
}).catch((err: BusinessError) => {
  console.error("get file sync state failed with error message: " + err.message + ", error code: " + err.code);
});

```

## cloudSync.getFileSyncState<sup>11+</sup>

getFileSyncState(uri: Array&lt;string&gt;, callback: AsyncCallback&lt;Array&lt;FileSyncState&gt;&gt;): void

Obtains the file sync state. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | Array&lt;string&gt; | Yes  | URI of the file whose sync state is to be obtained.|
| callback | AsyncCallback&lt;Array&lt;FileSyncState&gt;&gt; | Yes  | Callback used to return the file sync state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |
| 13900002  | No such file or directory. |
| 14000002  | Invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let uris: Array<string> = ["file://uri"];
cloudSync.getFileSyncState(uris, (err: BusinessError, syncStates: Array<cloudSync.FileSyncState>) => {
  if (err) {
    console.error("get file sync state with error message: " + err.message + ", error code: " + err.code);
  } else {
    syncStates.forEach((item) => {
      console.info("get file sync state successfully" + item);
    })
  }
});
```

## cloudSync.getFileSyncState<sup>12+</sup>

getFileSyncState(uri: string): FileSyncState

Obtains the file sync state.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| uri | string | Yes  | URI of the target file.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| [FileSyncState](#filesyncstate11) | Sync state of the file.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13900002  | No such file or directory. |
| 13900004  | Interrupted system call. |
| 13900010  | Try again. |
| 13900012  | Permission denied by the file system. |
| 13900031  | Function not implemented. |
| 13900042  | Unknown error. |
| 14000002  | Invalid uri. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
try {
  let state = cloudSync.getFileSyncState(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("getFileSyncStatefailed with error: " + JSON.stringify(error));
}
```

## FileSyncState<sup>11+</sup>

Enumerates the device-cloud file sync states.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name|  Value|  Description|
| ----- |  ---- |  ---- |
| UPLOADING |  0 | The file is being uploaded.|
| DOWNLOADING |  1 | The file is being downloaded.|
| COMPLETED |  2 | Sync completed.|
| STOPPED |  3 | Sync stopped.|
| TO_BE_UPLOADED<sup>12+</sup> |  4 | The file is going to be uploaded.|
| UPLOAD_SUCCESS<sup>12+</sup> |  5 | The file has been successfully uploaded.|
| UPLOAD_FAILURE<sup>12+</sup> |  6 | The file fails to be uploaded.|

## cloudSync.optimizeStorage<sup>17+</sup>

optimizeStorage(): Promise&lt;void&gt;

Optimizes the resources that have been synced to the cloud from the local Gallery and executes the automatic aging policy according to the remaining local space. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Return value**

  | Type                 | Description                          |
  | ------------------- | ---------------------------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. 2.Incorrect parameter types. |
| 13600001  | IPC error. |
| 13900042  | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

cloudSync.optimizeStorage().then(() => {
  console.info("optimize storage successfully");   // The foreground UX waits for blocking operations to complete.
}).catch((err: BusinessError) => {
  console.error("optimize storage failed with error message: " + err.message + ", error code: " + err.code);
});
```

## cloudSync.startOptimizeSpace<sup>17+</sup>

startOptimizeSpace(optimizePara: OptimizeSpaceParam, callback?: Callback\<OptimizeSpaceProgress>): Promise&lt;void&gt;

Optimizes local resources that have been synced to the cloud and optimizes local images and videos that have not been accessed before the aging period expires. This API uses a promise to return the result. The callback returns the optimization progress.

**startOptimizeSpace** is used together with **stopOptimizeSpace**. If **startOptimizeSpace** is called repeatedly, the error code 22400006 will be returned, indicating that other tasks are being executed.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| optimizePara | [OptimizeSpaceParam](#optimizespaceparam17) | Yes  | Optimizes parameters.|
| callback | Callback&lt;[OptimizeSpaceProgress](#optimizespaceprogress17)&gt; | No  | Callback used to return the optimization progress. By default, error code 401 is returned and no clearing task is executed.|

**Return value**

  | Type                 | Description                          |
  | ------------------- | ---------------------------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. |
| 22400005  | Inner error. |
| 22400006  | The same task is already in progress. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let para:cloudSync.OptimizeSpaceParam = {totalSize: 1073741824, agingDays: 30};
let callback = (data:cloudSync.OptimizeSpaceProgress) => {
  if (data.state == cloudSync.OptimizeState.FAILED) {
    console.error("optimize space failed");
  } else if (data.state == cloudSync.OptimizeState.COMPLETED && data.progress == 100) {
    console.info("optimize space successfully");
  } else if (data.state == cloudSync.OptimizeState.RUNNING) {
    console.info("optimize space progress: " + data.progress);
  }
}
cloudSync.startOptimizeSpace(para, callback).then(() => {
  console.info("start optimize space");
}).catch((err: BusinessError) => {
  console.error("start optimize space failed with error message: " + err.message + ", error code: " + err.code);
});
```

## cloudSync.stopOptimizeSpace<sup>17+</sup>

stopOptimizeSpace(): void

Synchronously stops optimizing cloud resource space. This method is used with **startOptimizeSpace**.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 13600001  | IPC error. |
| 22400005  | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let para:cloudSync.OptimizeSpaceParam = {totalSize: 1073741824, agingDays: 30};
let callback = (data:cloudSync.OptimizeSpaceProgress) => {
  if (data.state == cloudSync.OptimizeState.FAILED) {
    console.error("optimize space failed");
  } else if (data.state == cloudSync.OptimizeState.RUNNING) {
    console.info("optimize space progress: " + data.progress);
  }
}
cloudSync.startOptimizeSpace(para, callback);
cloudSync.stopOptimizeSpace();   // Stop space optimization.
```

## OptimizeState<sup>17+</sup>

Enumerates the space optimization states.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name|  Value|  Description|
| ----- |  ---- |  ---- |
| RUNNING |  0 | The space is being optimized.|
| COMPLETED |  1 | The space optimization is complete.|
| FAILED |  2 | Space optimization failed.|
| STOPPED |  3 | Space optimization stopped.|

## OptimizeSpaceProgress<sup>17+</sup>

Represents the space optimization states and optimization progress.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name    | Type  | Read-Only| Optional| Description|
| ---------- | ------ | ---- | ---- | ---- |
| state | [OptimizeState](#optimizestate17) | No  | No  | Enumerates the space optimization states.|
| progress | number | No  | No  | Optimization progress percentage. The value range is [0, 100].|

## OptimizeSpaceParam<sup>17+</sup>

Sets the total optimization space and aging days.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name    | Type  | Read-Only| Optional| Description|
| ---------- | ------ | ---- | ---- | ---- |
| totalSize | number | No  | No  | Total size of the optimization space. You can obtain the total size of all files to be aged through the media library API. The size is transferred by the application and is in bytes.|
| agingDays | number | No  | No  | Aging days. The system optimizes the local images and videos that have been uploaded to the cloud but not viewed for more than the aging days.|

## UploadProgress

File upload progress information.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name     | Type   | Read-Only | Optional | Description |
| ---------- | ------ | ---- | ---- | ---- |
| state | [UploadState](#uploadstate) | No   | No   | File upload status. |
| processed | number | No   | No   | Size of the uploaded data. The value range is [0, 9223372036854775807], in bytes. |
| size | number | No   | No   | Total size of the current file. The value range is [0, 9223372036854775807], in bytes. |
| uri | string | No   | No   | URI of the current file. |
| error | [ErrorType](./js-apis-file-cloudsync.md#errortype12) | No   | No   | Error type of the upload. |

## UploadState

Enumerates the file upload states.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name |  Value |  Description |
| ----- |  ---- |  ---- |
| WAITING |  0 | Waiting for upload. |
| RUNNING |  1 | Uploading. |
| COMPLETED |  2 | Upload completed. |
| FAILED |  3 | Upload failed. |
| STOPPED |  4 | Upload stopped. |
| PAUSED |  5 | Upload paused. |

## ErrorType<sup>12+</sup>

Enumerates the file upload failure types.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API**: This is a system API.

| Name |  Value|  Description |
| ----- |  ---- |  ---- |
| RESPONSE_TIME_OUT |  9 | Cloud service timeout.<br>**Since Version**: 26.0.0 |
| UNKNOWN_ERROR |  10 | Unknown error.<br>**Since Version**: 26.0.0 |