# FileVersion

```TypeScript
class FileVersion
```

Represents the device-cloud file version management class. It allows you to manage historical versions of client- cloud files, obtain the list of historical versions, download historical versions to the local device, replace the current local file with a historical version file, and query and remove conflict flags for version conflicts.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## clearFileConflict

```TypeScript
clearFileConflict(uri: string): Promise<void>
```

Clears the version conflict flag of the local file. If a conflict occurs, you need to call this API to clear the conflict flag after the conflict is resolved locally and trigger automatic synchronization. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file for which the conflict flag is to be cleared. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

let isConflict = false;
fileVersion.isFileConflict(uri).then((isConflictRet: boolean) => {
  isConflict = isConflictRet;
  console.info("current file is conflict: " + isConflictRet);
}).catch((err: BusinessError) => {
  console.error(`get current file conflict flag failed with error message: ${err.message}, error code: ${err.code}`);
});
fileVersion.clearFileConflict(uri).then(() => {
  console.info("clean file conflict flag success");
}).catch((err: BusinessError) => {
  console.error("clean file conflict flag failed with error message: " + err.message + ", error code: " + err.code);
});
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **FileVersion** instance.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
let fileVersion = new cloudSync.FileVersion();
```

## downloadHistoryVersion

```TypeScript
downloadHistoryVersion(uri: string, versionId: string, callback: Callback<VersionDownloadProgress>): Promise<string>
```

Obtains the content of a file of a specified version based on the version number. You can download a file of a specified version from the cloud to a temporary local path. The application determines whether to replace the original file with the temporary file, or retain or delete the temporary file. The callback returns the file download progress, and the promise returns the URI of the temporary file of an earlier version.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | File URI. |
| versionId | string | Yes | Version ID of a file. The format is returned by the [gethistoryversionlist](#gethistoryversionlist) API. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VersionDownloadProgress](arkts-corefile-cloudsync-versiondownloadprogress-i.md)&gt; | Yes | Callback used to return the download progress. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the temporary file of a historical version. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400002 | Network unavailable. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let versionId = '123456'; // The format returned by the getHistoryVersionList method is used as an example.

let callback = (data: cloudSync.VersionDownloadProgress) => {
  if (data.state == cloudSync.State.RUNNING) {
    console.info("download progress: " + data.progress);
  } else if (data.state == cloudSync.State.FAILED) {
    console.info("download failed errType: " + data.errType);
  } else if (data.state == cloudSync.State.COMPLETED) {
    console.info("download version file success");
  }
};

fileVersion.downloadHistoryVersion(uri, versionId, callback).then((fileUri: string) => {
  console.info("success to begin download, downloadFileUri: " + fileUri);
}).catch((err: BusinessError) => {
  console.error("download history version file failed with error message: " + err.message + ", error code: " + err.code);
});
```

## getHistoryVersionList

```TypeScript
getHistoryVersionList(uri: string, versionNumLimit: number): Promise<Array<HistoryVersion>>
```

Obtains the list of historical versions. The returned versions are sorted by modification time. The earlier the modification time, the later the version. This API uses a promise to return the result.

If the number of cloud versions is less than the length limit, the list will be returned with the actual number of versions.

If the number of cloud versions is greater than or equal to the length limit, the number of the latest versions (specified by **versionNumLimit**) will be returned.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | File URI. |
| versionNumLimit | number | Yes | Length limit of the historical version list. The value range is [0, 100000] (unit: number). If the input value is greater than 100,000, the list is returned according to the maximum value. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[HistoryVersion](arkts-corefile-cloudsync-historyversion-i.md)&gt;&gt; | Promise used to return the list of historical versions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400002 | Network unavailable. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let limit = 10;

fileVersion.getHistoryVersionList(uri, limit).then((versionList: Array<cloudSync.HistoryVersion>) => {
  for(let i = 0, len = versionList.length; i < len; i++) {
    console.info("get history versionId: " + versionList[i].versionId);
  }
}).catch((err: BusinessError) => {
  console.error("get history version failed with error message: " + err.message + ", error code: " + err.code);
});
```

## isFileConflict

```TypeScript
isFileConflict(uri: string): Promise<boolean>
```

Obtains the version conflict flag of a local file. This API uses a promise to return the result. This API takes effect only when the application is configured for manual conflict resolution. Otherwise, conflicts are automatically resolved during synchronization, and the return value will be **false**.

Once the application is configured for manual conflict resolution, calling this API returns whether the current local file conflicts with the cloud file. The application then prompts the user to handle the conflict. After the conflict is resolved, you need to call the [clearFileConflict](#clearfileconflict) method to clear the conflict flag and synchronize the file to the cloud.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | File URI. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the conflict flag between the local file and the cloud file. The value **true** indicates that the local file conflicts with the cloud file, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileVersion.isFileConflict(uri).then((isConflict: boolean) => {
  console.info("current file is conflict: " + isConflict);
}).catch((err: BusinessError) => {
  console.error("get current file conflict flag failed with error message: " + err.message + ", error code: " + err.code);
});
```

## replaceFileWithHistoryVersion

```TypeScript
replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise<void>
```

Replaces the local file with the file of a historical version. Before replacement, call the [downloadHistoryVersion](#downloadhistoryversion) method to download the selected historical version and obtain its version URI. If this API is called directly without prior download or the version URI is invalid, an exception will be thrown. Once replacement is complete, the temporary file will be automatically deleted. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| originalUri | string | Yes | URI of the local file. |
| versionUri | string | Yes | URI of the historical file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. Possible causes: 1.originalUri invalid; 2.versionUri invalid. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 22400007 | The version file specified to replace the original file does not exist. |

**Examples**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let versionId = '123456'; // The format returned by the getHistoryVersionList method is used as an example.

let callback = (data: cloudSync.VersionDownloadProgress) => {
  if (data.state == cloudSync.State.RUNNING) {
    console.info("download progress: " + data.progress);
  } else if (data.state == cloudSync.State.FAILED) {
    console.info("download failed errType: " + data.errType);
  } else if (data.state == cloudSync.State.COMPLETED) {
    console.info("download version file success");
  }
};

let versionUri = "";
fileVersion.downloadHistoryVersion(uri, versionId, callback).then((fileUri: string) => {
  versionUri = fileUri;
  console.info("success to begin download, downloadFileUri: " + fileUri);
}).catch((err: BusinessError) => {
  console.error(`download history version file failed with error message: ${err.message}, error code: ${err.code}`);
});
fileVersion.replaceFileWithHistoryVersion(uri, versionUri).then(() => {
  console.info("replace file with history version success.");
}).catch((err: BusinessError) => {
  console.error("replace file with history version failed with error message: " + err.message + ", error code: " + err.code);
});
```
