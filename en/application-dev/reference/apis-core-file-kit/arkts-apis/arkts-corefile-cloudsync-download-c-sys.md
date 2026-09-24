# Download (System API)

```TypeScript
class Download
```

Provides APIs for downloading image files to **Gallery**. Before using the APIs of **Download**, you need to create a **Download** instance.

**Since:** 10

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Download** instance.

**Since:** 10

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Examples**

```TypeScript
let download = new cloudSync.Download()
```

## off

```TypeScript
off(evt: 'progress', callback: (pg: DownloadProgress) => void): void
```

Removes the specified callback from the device-cloud download progress.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| evt | 'progress' | Yes | Event type. The value is **progress**, which indicates the sync progress event. |
| callback | (pg: DownloadProgress) =&gt; void | Yes | Callback used to return the file download progress. The input parameter is [DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md), and the return value is **void**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**Examples**

```TypeScript
let download = new cloudSync.Download();

let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
}

download.on('progress', callback);

download.off('progress', callback);
```

<a id="off-1"></a>

## off

```TypeScript
off(evt: 'progress'): void
```

Removes all callbacks from the device-cloud download progress.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| evt | 'progress' | Yes | Event type. The value is **progress**, which indicates the download progress event of a cloud file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**Examples**

```TypeScript
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
});

download.off('progress');
```

## on

```TypeScript
on(evt: 'progress', callback: (pg: DownloadProgress) => void): void
```

Registers a listener for the download progress of a cloud file.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| evt | 'progress' | Yes | Event. The value is **progress**, which indicates the download progress event of a cloud file. |
| callback | (pg: DownloadProgress) =&gt; void | Yes | Callback used to return the file download progress. The input parameter is [DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md), and the return value is **void**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error |

**Examples**

```TypeScript
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});
```

## start

```TypeScript
start(uri: string): Promise<void>
```

Starts downloading a cloud file. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |

**Examples**

```TypeScript
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

<a id="start-1"></a>

## start

```TypeScript
start(uri: string, callback: AsyncCallback<void>): void
```

Starts downloading a cloud file. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the target file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to start downloading a cloud file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900025 | No space left on device. |

**Examples**

```TypeScript
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

## stop

```TypeScript
stop(uri: string): Promise<void>
```

Stops downloading a cloud file. This API uses a promise to return the result.

> **NOTE:** 
> 
> Calling **stop** will terminate the download of the current file and clear the cache file. You can use
> **start** to start the download again.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(uri: string, callback: AsyncCallback<void>): void
```

Stops downloading a cloud file. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Calling **stop** will terminate the download of the current file and clear the cache file. You can use
> **start** to start the download again.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the target file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to stop downloading a cloud file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**Examples**

```TypeScript
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
