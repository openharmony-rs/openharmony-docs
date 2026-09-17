# CloudFileCache

Provides APIs for the file manager application to download files from the Drive Kit to a local device.

**Since:** 11

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## cleanCache

```TypeScript
cleanCache(uri: string): void
```

Deletes a cache file. This API returns the result synchronously.

**Since:** 11

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the cache file to delete. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
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

try {
  fileCache.cleanCache(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("clean cache failed with error message: " + err.message + ", error code: " + err.code);
}
```

## constructor

```TypeScript
constructor(bundleName: string)
```

A constructor used to create a CloudFileCache object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the bundle that need to start download task and subscribes download progress. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |

## getDownloadList

```TypeScript
getDownloadList(uris: Array<string>): Promise<Array<DownloadProgress>>
```

Query the download state of the cloud file list.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDFILE_SYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | Yes | uris of queryed files. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md)&gt;&gt; | Return Promise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified. 2.The length of the input parameter exceeds the upper limit. <br>3.The input parameter contains an invalid uri. |
