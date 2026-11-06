# @ohos.file.backup (Backup and Restore) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=43cd69d89ed4f07acd685a4381dc8b048910320c translatedAt=2026-11-03T04:03:43.083Z pushedAt=2026-11-04T03:11:33.502Z nl=1 -->

This module provides applications with the capability of backing up and restoring data, addressing data preservation and recovery in scenarios such as application data migration, system upgrade, and device replacement. A tool application can perform full backup through SessionBackup, perform restoration through SessionRestore, and perform incremental backup through IncrementalBackupSession. The backup service notifies applications of the backup/restore phase, file handle, progress, and result through GeneralCallbacks.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { backup } from '@kit.CoreFileKit';
```

## FileMeta

Metadata of a file, including an application name and a file URI. FileMeta is an indispensable object when performing backup/restore.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name       | Type   | Read-Only | Optional | Description                                                                                                |
| ---------- | ------ | ---- | ---- |--------------------------------------------------------------------------------------------------- |
| bundleName | string | No   | No | Application name, which can be obtained through the method provided by [bundleManager.BundleInfo](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md). The backup service locates and processes the data of the corresponding application based on this name. |
| uri        | string | No   | No | Name of the file to be transferred in the application sandbox. Currently, uri has not been upgraded to the standard format, and only names composed of 0-9a-zA-Z, underscores (_), and periods (.) are accepted. The backup service locates and processes the data of the corresponding application based on this name.      |
| uris        | Array&lt;string&gt; | No   | Yes | Array of names of the files to be transferred in the application sandbox. Currently, uris has not been upgraded to the standard format, and only names composed of 0-9a-zA-Z, underscores (_), and periods (.) are accepted.<br>**Model Constraint**: This API can be used only in the stage model.<br>**Since Version**: 26.0.0      |

## FileData

Metadata of a file, including an opened file descriptor. FileData is an indispensable object when performing backup/restore.

> **NOTE**
>
> FileData must be closed after use. Otherwise, a memory leak will occur. For the closing method, refer to the related closing APIs such as [fileIo.closeSync](js-apis-file-fs.md#fileioclosesync) provided by [@ohos.file.fs](js-apis-file-fs.md).

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name | Type   | Read-Only | Optional | Description                                     |
| ---- | ------ | ---- | --- |---------------------------------------- |
| fd   | number | No   | No | Opened file descriptor, obtained through the backup service, which can be used to read or write backup/restore file content. |

## FileManifestData<sup>12+</sup>

Metadata of a file, containing an already opened file descriptor. The content opened by FileManifestData is a manifest file, which is used to describe the basic information of the corresponding file during incremental backup/restore of an application. During incremental backup, the Backup Service reads the manifest file based on manifestFd, compares the last incremental time with the basic file information, and identifies the incremental files that need to be processed. FileManifestData is an indispensable object when performing incremental backup/restore.

> **NOTE**
>
> FileManifestData must be closed after use. Otherwise, a memory leak will occur. For details about how to close it, see [fileIo.closeSync](js-apis-file-fs.md#fileioclosesync) and other close APIs.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name       | Type   | Read-Only | Optional | Description                                     |
| ---------- | ------ | ---- | --- | ---------------------------------------- |
| manifestFd | number | No   | No | An already opened file descriptor, obtained through the Backup Service. |

## IncrementalBackupTime<sup>12+</sup>

Used to record the time of the last incremental backup, describing the time point of the backup increment.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name                | Type   | Read-Only | Optional | Description                                                                                                |
| ------------------- | ------ | --------- | -------- | ---------------------------------------------------------------------------------------------------------- |
| bundleName          | string | No        | No       | Application name, which can be obtained through the method provided by [bundleManager.BundleInfo](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md). |
| lastIncrementalTime | number | No        | No       | Time of the last incremental backup.                                                                        |

## BackupParams<sup>12+</sup>

Provides optional configuration parameters for backup and restore, in the form of a JSON-format string.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name       | Type   | Read-Only | Optional | Description                                               |
| ---------- | ------ | ---- | ---- | -------------------------------------------------- |
| parameters | string | No   | Yes | A string with JSON-format configuration items, providing optional options for backup and restore. The fields are agreed upon by the backup and restore service. The default value is empty, indicating that no additional configuration is used. |

## BackupPriority<sup>12+</sup>

Provides priority configuration for backup and restore. When multiple applications are backed up or restored simultaneously, this configuration can be used to make applications with higher priority execute first.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name     | Type   | Read-Only | Optional | Description                                                   |
| -------- | ------ | ---- | ---- | ------------------------------------------------------ |
| priority | number | No   | Yes | A larger value indicates a higher priority. When the priorities are the same, the one called first is executed first. The default value is 0. |

## IncrementalBackupData<sup>12+</sup>

An object for a single incremental backup. It inherits [IncrementalBackupTime](#incrementalbackuptime12), [FileManifestData](#filemanifestdata12), [BackupParams](#backupparams12), and [BackupPriority](#backuppriority12).

> **Description:**
>
> Records the last incremental time of the application and the file descriptor of the incremental backup manifest file. The manifest file records the information of files that have been backed up within the incremental time. The backup service determines the file range that requires incremental processing based on lastIncrementalTime and manifestFd. parameters is used to pass additional configurations agreed upon by the business, and priority is used to control the backup/restore execution order of multiple applications.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

## File

A file object.

Inherits from [FileMeta](#filemeta) and [FileData](#filedata).

> **NOTE:**
>
> The file.backup.File differs in meaning from the [File](js-apis-file-fs.md#file) provided in @ohos.file.fs. The former is an object that inherits from [FileMeta](#filemeta) and [FileData](#filedata), while the latter is an object that contains only a file descriptor. Pay attention to the distinction and do not confuse them.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

## File<sup>12+</sup>

A file object.

Inherits from [FileMeta](#filemeta), [FileData](#filedata), and [FileManifestData](#filemanifestdata12).

> **NOTE**
>
> The file.backup.File differs in meaning from the [File](js-apis-file-fs.md#file) provided in @ohos.file.fs. The former is an object that inherits from [FileMeta](#filemeta), [FileData](#filedata), and [FileManifestData](#filemanifestdata12), while the latter is an object that contains only a file descriptor. Be sure to distinguish between them and avoid confusion.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

## FileSystemRequestConfig<sup>23+</sup>

Configures the parameters required for the system to perform fragment cleanup.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name        | Type   | Read-Only | Optional | Description                                                   |
| ----------- | ------ | ---- | ---- | ------------------------------------------------------ |
| triggerType | number |  No  |  No  | API version 23 supports only trigger type 0, which specifies the trigger type of fragment cleanup and indicates performing the storage device fragment cleanup function to clean up fragment space and improve storage performance. Other values return a parameter error.<br>Starting from API version 26.0.1, trigger types 1, 2, and 3 for IO storage optimization are supported.<br>1 indicates enabling the IO space-for-performance policy;<br>2 indicates disabling the IO space-for-performance policy;<br>3 indicates querying the IO space-for-performance policy;<br>Other values return a parameter error.|
| writeSize   | number |  No  |  No  | When the trigger type is 0, it represents the cleanup target of the fragment cleanup function, that is, the expected available storage units of the target size that can be cleaned up.<br>When the trigger type is 1, 2, or 3, it represents the target of IO storage optimization, that is, the expected target size above which storage optimization is performed.<br>Unit: MB. Value range: 0-2097152 MB. Values outside this range return a parameter error.|
| waitTime    | number |  No  |  No  | When the trigger type is 0, it represents the maximum allowed time for executing the fragment cleanup function. If this time is exceeded, the task is considered timed out. Unit: s. Value range: [0, 300]. Values outside this range return a parameter error.<br>When the trigger type is 1 or 2, this parameter is not considered.<br>When the trigger type is 3, it represents the interval query time of IO storage optimization. Each time the interval query time is reached, a query of the IO space-for-performance policy is triggered. Unit: ms. Value range: [0, +∞).|

## PathInfo

Path information for file migration.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**System API**: This is a system API.

| Name       | Type   | Read-Only | Optional | Description                                     |
| ---------- | ------ | ---- | --- | ---------------------------------------- |
| srcPath | string | No   | No | Source path of the migration. The length is limited to 4096 characters. Relative paths and soft links are not supported. If the length limit is exceeded, a parameter error is returned. |
| destPath | string | No   | No | Destination path of the migration. The length is limited to 4096 characters. Relative paths and soft links are not supported. If the length limit is exceeded, a parameter error is returned. |

## GeneralCallbacks

Common callbacks during the backup/restore process. The Backup Service uses these callbacks to notify the client of the backup/restore phase of its application.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

### Attributes

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| onFileReady | AsyncCallback&lt;[File](#file)&gt; | No | No | Callback for the server to send a file to the client. When the sending succeeds, err is undefined and data is [File](#file); otherwise, it is an error object. The File in the AsyncCallback belongs to the file.backup.[File](#file) type. The returned file is owned by the Backup Service, and the client must close the File Handle after the file operation is complete.<br>After the File Handle is closed, the Backup Service cleans up the file in the subsequent process.<br>**Error Codes**:<br>For details about the following error codes, see [File Management Error Codes](errorcode-filemanagement.md).<br>- 13600001: IPC error.<br>- 13900005: I/O error.<br>- 13900011: Out of memory.<br>- 13900020: Invalid argument.<br>- 13900025: No space left on device.<br>- 13900042: Unknown error. |
| onBundleBegin | AsyncCallback&lt;string, void \| string&gt; | No | No | Callback triggered when Application Backup/Restore starts. When the operation succeeds, err is undefined and data is the bundle name of the application whose backup/restore is currently starting; otherwise, it is an error object.<br>Since API version 12, when err is returned, the second string parameter bundleName is also returned.<br>Developers can use this return value to record the start state of the current application's backup/restore, initialize progress display, or prepare for subsequent processing.<br>**Error Codes**:<br>For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).<br>- 401: Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>- 13500001: The application is not added to the backup or restore.<br>- 13500002: Failed to start application extension Procedure.<br>- 13600001: IPC error.<br>- 13900005: I/O error.<br>- 13900011: Out of memory.<br>- 13900025: No space left on device.<br>- 13900042: Unknown error. |
| onBundleEnd | AsyncCallback&lt;string, void \| string&gt; | No | No | Callback triggered when Application Backup/Restore ends. When the operation succeeds, err is undefined and data is the bundle name of the application whose backup/restore is currently ending; otherwise, it is an error object.<br>Since API version 12, when err is returned, the second string parameter bundleName is also returned.<br>Developers can use this return value to record the end state of the current application's backup/restore, update the result display, or clean up temporary state.<br>**Error Codes**:<br>For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).<br>- 401: Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>- 13500003: Backup or restore timed out.<br>- 13500004: Application extension death.<br>- 13600001: IPC error.<br>- 13900005: I/O error.<br>- 13900011: Out of memory.<br>- 13900025: No space left on device.<br>- 13900042: Unknown error. |
| onAllBundlesEnd | AsyncCallback&lt;undefined&gt; | No | No | Callback triggered when the backup/restore process of all bundles ends. When the operation succeeds, err is undefined; otherwise, it is an error object. No return result.<br>**Error Codes**:<br>For details about the following error codes, see [File Management Error Codes](errorcode-filemanagement.md).<br>- 13600001: IPC error.<br>- 13900005: I/O error.<br>- 13900011: Out of memory.<br>- 13900020: Invalid argument.<br>- 13900025: No space left on device.<br>- 13900042: Unknown error. |
| onBackupServiceDied | Callback&lt;undefined&gt; | No | No | Callback triggered when the Backup Service dies abnormally. No return result. |
| onBackupSizeReport<sup>18+</sup>  | [OnBackupSizeReport](#onbackupsizereport18) | No | Yes |  Used together with getBackupDataSize to return the information about the amount of data to be backed up. When this callback is not set, the data size scan result is not received. |
| onMigrateResult | AsyncCallback&lt;string, void \| string&gt; | No | Yes | Callback for the end of the file migration process, returning the result information of the migrated file. When the migration operation succeeds, err is undefined and data is string (Application Name); otherwise, it is an error object. When this callback is not set, the file migration result is not received.<br>**Since Version**: 26.0.0<br>**Model Constraint**: This API can be used only in the stage model.<br>**Error Codes**:<br>For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).<br>- 202: Permission verification failed, application which is not a system application uses system API.<br>- 13600001: IPC error.<br>- 13900001: Operation not permitted.<br>- 13900005: I/O error.<br>- 13900011: Out of memory.<br>- 13900020: Invalid argument.<br>- 13900025: No space left on device. |
| onFileReadyBatch | [OnFileReadyBatch](#onfilereadybatch) | No | Yes | Callback triggered when a batch of files is ready to be sent to the client.<br>**Since Version**: 26.0.0<br>**Model Constraint**: This API can be used only in the stage model.<br>**Error Codes**:<br>For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).<br>- 202: Permission verification failed, application which is not a system application uses system API.<br>- 13600001: IPC error.<br>- 13900005: I/O error.<br>- 13900011: Out of memory.<br>- 13900020: Invalid argument.<br>- 13900025: No space left on device. |

### onResultReport<sup>12+</sup>

onResultReport(bundleName: string, result: string): void

Callback function. When application backup/restore ends, if the callback is successfully triggered, the application bundle name and application backup/restore information (backup/restore count or exception information, etc.) are returned.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type   | Mandatory | Description                            |
| -------------- | ------ | --------- | -------------------------------------- |
| bundleName     | string | Yes       | Pointer to the application bundle name.               |
| result         | string | Yes       | Application backup/restore information returned in JSON format, including backup/restore count or exception information, etc. It can be used to determine the backup/restore result and display it to users. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.               |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.           |

**Example**

  ```ts
  import { backup } from '@kit.CoreFileKit';

  onResultReport: (bundleName: string, result: string) => {
    console.info('onResultReport bundleName : ' + bundleName);
    console.info('onResultReport result : ' + result);
  }
  ```

### onProcess<sup>12+</sup>

onProcess(bundleName: string, process: string): void

Callback function. Reports progress information during the application backup/restore process, returning the progress information and exception information of the application's business execution.

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type   | Mandatory | Description                            |
| -------------- | ------ | --------- | -------------------------------------- |
| bundleName     | string | Yes       | Pointer to the application bundle name.              |
| process        | string | Yes       | Returns the progress information of the application backup/restore in JSON format, which may include the progress percentage, the number of completed files, or exception information, for displaying the backup/restore progress. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13500006 | Tar error.               |
| 13500008 | Untar error.               |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted.               |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900020 | Invalid argument.           |
| 13900025 | No space left on device. |

**Example**

  ```ts
  import { backup } from '@kit.CoreFileKit';

  onProcess: (bundleName: string, process: string) => {
    console.info('onProcess bundleName : ' + bundleName);
    console.info('onProcess processInfo : ' + process);
  }
  ```

## backup.fileSystemServiceRequest<sup>23+</sup>

fileSystemServiceRequest(config: FileSystemRequestConfig): Promise&lt;number&gt;

Defragments the fragmented space of a storage device to improve the user experience of lag. It is applicable to scenarios where storage space is tight, storage performance degrades, or proactive storage maintenance is required. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**
| Name   | Type                                       | Mandatory | Description                                               |
| -------- | ------------------------------------------ | ---- | -------------------------------------------------- |
|  config  | [FileSystemRequestConfig](#filesystemrequestconfig23)| Yes | Parameters required for the system to perform fragment cleanup. After being set, a fragment cleanup task is triggered, and the cleanup type, target size, and maximum execution time are controlled by triggerType, writeSize, and waitTime. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;number&gt;  | Promise object that returns the error code generated when the fragment cleanup operation is executed. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13900020 | Invalid argument.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { backup } from '@kit.CoreFileKit';

async function testFunction(size: number) {
  try {
    const result = await backup.fileSystemServiceRequest({
      triggerType: 0,
      writeSize: size,
      waitTime: 180
    });
    console.info(`fileSystemServiceRequest result: ${result}`);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`fileSystemServiceRequest err:` + err);
  }
}
```

## backup.getBackupVersion<sup>18+</sup>

getBackupVersion(): string

Obtains the backup and restore version information, which can be used to confirm the current backup and restore framework version, perform version compatibility checks, or compare capabilities before and after an upgrade.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| string | Returns the backup and restore version information.<br/>The version number is in the format of "API version.internal version". For example, the version number corresponding to API 16 is 16.0. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { backup } from '@kit.CoreFileKit';

  function getBackupVersion() {
    try {
      let result = backup.getBackupVersion();
      console.info('getBackupVersion success, result: ' + result);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getBackupVersion failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

**Content example:**

  ```json
  { "backupVersion" : "16.0" }
  ```

## backup.getLocalCapabilities

getLocalCapabilities(callback: AsyncCallback&lt;FileData&gt;): void

Obtains a JSON file that describes local capabilities. It can be used to confirm whether an application supports backup before backup, verify capability matching before restore, or generate the capability file required for restore. This API uses an asynchronous callback.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                                       | Mandatory | Description                                               |
| --------- | ------------------------------------------ | --------- | -------------------------------------------------- |
| callback  | AsyncCallback&lt;[FileData](#filedata)&gt; | Yes       | Callback invoked after the local capability file is obtained asynchronously. Returns a FileData object. The file descriptor in it must be closed after use. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.          |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  try {
    backup.getLocalCapabilities((err: BusinessError, fileData: backup.FileData) => {
      if (err) {
        console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('getLocalCapabilities success');
      console.info('fileData info:' + fileData.fd);
      fileIo.closeSync(fileData.fd);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
  }
  ```

**The capability file can be obtained through related APIs such as [fileIo.stat](js-apis-file-fs.md#fileiostat) provided by [@ohos.file.fs](js-apis-file-fs.md). Example of the capability file content:**

 ```json
 {
  "backupVersion" : "16.0",
  "bundleInfos" :[{
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

## backup.getLocalCapabilities

getLocalCapabilities(): Promise&lt;FileData&gt;

Obtains a JSON file that describes local capabilities. It can be used to confirm whether an application supports backup before backup, to verify capability matching before restore, or to generate the capability file required for restore. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                                 | Description                            |
| ------------------------------------ | ------------------------------- |
| Promise&lt;[FileData](#filedata)&gt; | Promise object that returns a FileData object, which contains the file descriptor for reading the content of the local capability file. The file descriptor must be closed after use. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.           |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  async function getLocalCapabilities() {
    try {
      let fileData = await backup.getLocalCapabilities();
      console.info('getLocalCapabilities success');
      console.info('fileData info:' + fileData.fd);
      fileIo.closeSync(fileData.fd);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

  **The capability file can be obtained through related APIs such as [fileIo.stat](js-apis-file-fs.md#fileiostat) provided by [@ohos.file.fs](js-apis-file-fs.md). An example of the capability file content is as follows:**

 ```json
 {
  "backupVersion" : "16.0",
  "bundleInfos" :[{
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

## backup.getLocalCapabilities<sup>12+</sup>

getLocalCapabilities(dataList:Array&lt;IncrementalBackupTime&gt;): Promise&lt;FileData&gt;

Obtains a JSON file that describes local capabilities. Based on the parameters passed in dataList, it queries the local capability data of the corresponding application. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                                                           | Mandatory | Description                                           |
| --------- | -------------------------------------------------------------- | --------- | ---------------------------------------------- |
| dataList | Array&lt;[IncrementalBackupTime](#incrementalbackuptime12)&gt; | Yes   | List of incremental backup data, used to describe the application to be queried and the last incremental backup time. |

**Return value**

| Type                                 | Description                            |
| ------------------------------------ | ------------------------------- |
| Promise&lt;[FileData](#filedata)&gt; | Promise object that returns a FileData object, which contains the file descriptor for reading the local capability file content. The file descriptor must be closed after use. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.                                                                                      |
| 13900005 | I/O error.                                                                                      |
| 13900011 | Out of memory.                                                                                  |
| 13900025 | No space left on device.                                                                        |
| 13900042 | Unknown error.                                                                                  |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  async function getLocalCapabilities() {
    try {
      let backupApps: backup.IncrementalBackupTime[] = [{
        bundleName: 'com.example.hiworld',
        lastIncrementalTime: 1700107870 // Record the incremental backup time based on the caller's last record.
      }];
      let fileData = await backup.getLocalCapabilities(backupApps);
      console.info('getLocalCapabilities success');
      console.info('fileData info:' + fileData.fd);
      fileIo.closeSync(fileData.fd);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

## backup.getBackupInfo<sup>12+</sup>

getBackupInfo(bundleToBackup: string): string

Obtains the information of the application to be backed up. It can be used to confirm the application status before backup, obtain the backup details reported by the application, or troubleshoot backup issues.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleToBackup | string | Yes | Application Name to be backed up. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| string | Returns the backup information reported by the application. The specific content and format are customized by the application and can be used to describe the application status, backup scope, or other business information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { backup } from '@kit.CoreFileKit';

  function getBackupInfo() {
    try {
      let backupApp = 'com.example.hiworld';
      let result = backup.getBackupInfo(backupApp);
      console.info('getBackupInfo success, result: ' + result);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getBackupInfo failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

## backup.updateTimer<sup>12+</sup>

updateTimer(bundleName: string, timeout: number): boolean

Sets the duration for application backup or restore. The call timing is after onBundleBegin and before onBundleEnd. It is applicable to scenarios involving large-volume data backup or restore, unstable networks, or applications requiring longer processing time.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name for which the backup or restore duration is to be set. |
| timeout | number | Yes | Time limit for backup or restore. The input range is [0,14400000], in ms. A value out of range returns a parameter error. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| boolean | Whether the timeout is set successfully. true indicates success, and false indicates failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { backup } from '@kit.CoreFileKit';

  function updateTimer() {
    try {
      let timeout = 30000;
      let bundleName = 'com.example.hiworld';
      let result = backup.updateTimer(bundleName, timeout);
      if (result) {
        console.info('updateTimer success');
      } else {
        console.info('updateTimer fail');
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`updateTimer failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

## backup.updateSendRate<sup>12+</sup>

updateSendRate(bundleName: string, sendRate: number): boolean

Updates the rate at which the backup application sends file descriptors. The call timing is after onBundleBegin and before onBundleEnd. It applies to scenarios where network bandwidth is limited, the server processing capability is insufficient, or system overload needs to be avoided.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name          | Type     | Mandatory | Description                       |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes   | Application name for which the rate needs to be controlled. |
| sendRate | number | Yes   | File descriptor sending rate to be set for the application, in units of items per second, ranging from 0 to 800, with a default of 60 items per second. When it is 0, sending stops and resumes only when a non-zero value is set. If the set value exceeds the maximum of 800, sending proceeds at 800 items per second. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| boolean | Whether the sending rate is set successfully. true indicates success, and false indicates failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { backup } from '@kit.CoreFileKit';

  function updateSendRate() {
    try {
      let bundleName = 'com.example.myApp';
      let sendRate = 300;
      let result = backup.updateSendRate(bundleName, sendRate);
      if (result) {
        console.info('updateSendRate success');
      } else {
        console.info('updateSendRate fail');
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`updateSendRate failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

## OnBackupSizeReport<sup>18+</sup>

type OnBackupSizeReport = (reportInfo: string) => void

The size of the application data to be backed up, returned by the framework.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name   | Type                                  | Mandatory | Description                 |
| -------- | ------------------------------------- | ---- | -------------------- |
| reportInfo | string | Yes   | Information about the size of the application data to be backed up obtained by the framework, in JSON format string, containing the scanned and scanning fields. scanned indicates the list of application data sizes that have been scanned this time, and scanning indicates the bundle name of the application currently being scanned. Developers can parse it with JSON.parse before use. |

**Example**

  ```ts
  import { backup } from '@kit.CoreFileKit';

  onBackupSizeReport: (OnBackupSizeReport: backup.OnBackupSizeReport) => {
    console.info('dataSizeCallback success');
    console.info('dataSizeCallback report : ' + OnBackupSizeReport);
  }
  ```

## OnFileReadyBatch

type OnFileReadyBatch = (error: BusinessError&lt;void&gt;, files: Array&lt;[File](#file)&gt;) => void

Callback triggered when the server sends files back to the client.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**System API**: This is a system API.

**Parameters**

| Name     | Type   | Mandatory | Description                            |
| ---------- | ------ | ---- | ------------------------------- |
| error | BusinessError&lt;void&gt; | Yes   | When the file handle is obtained successfully, error is undefined; otherwise, it is an error object. |
| files     | Array&lt;[File](#file)&gt; | Yes   | When the file handle is obtained successfully, returns the array of obtained file handles. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  const onFileReadyBatch: backup.OnFileReadyBatch = (error: BusinessError<void>, files: Array<backup.File>): void => {
    if (error) {
      console.error(`onFileReadyBatch failed. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let file of files) {
      console.info(`onFileReadyBatch success with file: ${file.bundleName}, ${file.uri}`);
      fileIo.closeSync(file.fd);
    }
  };
  ```

## SessionBackup

A backup process object used to support the full backup process of applications. Before use, a SessionBackup instance must be created first. SessionBackup is suitable for scenarios where all application data needs to be backed up. IncrementalBackupSession is suitable for scenarios where only changed data is processed based on the last incremental backup time and the manifest file.

### constructor

constructor(callbacks: GeneralCallbacks)

Constructor of the backup process, used to obtain an instance of the SessionBackup class. The typical process is as follows: create a SessionBackup instance, call appendBundles to add the applications to be backed up, wait for the callback to return the backup result, and call release to release resources after the process ends.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                                  | Mandatory | Description                          |
| --------- | ------------------------------------- | --------- | ------------------------------------ |
| callbacks | [GeneralCallbacks](#generalcallbacks) | Yes       | Callbacks required by the backup process. |

**Example**

  ```ts
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
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create the backup process
  ```

### getLocalCapabilities<sup>18+</sup>

getLocalCapabilities(): Promise&lt;FileData&gt;

Obtains a JSON file that describes local capabilities during a backup operation. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                                 | Description                            |
| ------------------------------------ | ------------------------------- |
| Promise&lt;[FileData](#filedata)&gt; | Promise object that returns a FileData object, which contains the file descriptor for reading the content of the local capabilities file. The file descriptor must be closed after use. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error.                                                    |
| 13900001 | Operation not permitted.                                      |
| 13900020 | Invalid argument.                                             |
| 13900042 | Internal error.                                                |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  interface LocalCapabilities { // Used to parse the capabilities file
    bundleInfos: BundleInfo[];
    deviceType: string;
    systemFullName: string;
  }

  interface BundleInfo { // Used to obtain the local capability information of a single application
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

  let generalCallbacks: backup.GeneralCallbacks = { // Defines the general callbacks during the backup/restore process
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
    let sessionBackup = new backup.SessionBackup(generalCallbacks); // Creates a backup process
    let basePath = '/data/storage/el2/base/backup'; 
    let path = basePath + '/localCapabilities.json'; // Path for saving the capabilities file locally
    try {
      let fileData = await sessionBackup.getLocalCapabilities(); // Obtain the local capability file.
      if (fileData) {
        console.info('getLocalCapabilities success');
        console.info('fileData info:' + fileData.fd);
        if (!fileIo.accessSync(basePath)) {
          fileIo.mkdirSync(basePath);
          console.info('create success' + basePath);
        }
        fileIo.copyFileSync(fileData.fd, path); // Save the obtained local capability file to the local device.
        fileIo.closeSync(fileData.fd);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
    }
    let data = fileIo.readTextSync(path, 'utf8'); // Obtain information from the local capability file.
    try {
      const jsonsObj: LocalCapabilities | null = JSON.parse(data); // Parse the local capability file and print part of the information.
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

**The capability file can be obtained through related APIs such as [fileIo.stat](js-apis-file-fs.md#fileiostat) provided by [@ohos.file.fs](js-apis-file-fs.md). The following is an example of the capability file content:**

 ```json
 {
  "backupVersion" : "16.0",
  "bundleInfos" :[{
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

### getBackupDataSize<sup>18+</sup>

getBackupDataSize(isPreciseScan: boolean, dataList: Array\<IncrementalBackupTime\>): Promise&lt;void&gt;

Obtains the amount of data to be backed up for an application. It is called before appendBundles. It is used together with onBackupSizeReport, and the scan result is returned through the onBackupSizeReport callback. A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                                                     | Mandatory | Description                                                         |
| ------------- | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| isPreciseScan | boolean                                                  | Yes   | Whether to perform a precise scan. The value true indicates a precise scan, and false indicates a non-precise scan. A non-precise scan is fast and returns an estimated data amount. A precise scan is slow but returns a more accurate result. However, because the data to be backed up may change during the actual backup process, the precise scan result is not guaranteed to exactly match the actual backup data amount. |
| dataList      | Array<[IncrementalBackupTime](#incrementalbackuptime12)> | Yes   | List of applications to be backed up, used to describe the applications whose data amount is to be obtained and the time of the last backup (enter 0 for a full backup). |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 13600001 | IPC error.                                                    |
| 13900001 | Operation not permitted.                                      |
| 13900020 | Invalid argument.                                             |
| 13900042 | Internal error.                                                |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  interface ScannedInfos { // Used to parse the scan result.
    scanned: [];
    scanning: string;
  }

  interface ScannedInfo { // Used to parse the scan result of a single application.
    bundleName: string;
    dataSize: number;
    incDataSize: number;
  }

  let generalCallbacks: backup.GeneralCallbacks = { // Defines the general callbacks during the backup/restore process.
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
    },
    // The callback function is used together with getBackupDataSize and returns the obtained data amount of an application and the bundle name of the application whose data amount is being obtained.
    // The onBackupSizeReport in generalCallbacks returns the scan result every 5 seconds (or immediately if the scan is completed within 5 seconds) until the data amounts of all applications in dataList are returned.
    onBackupSizeReport: (OnBackupSizeReport) => {
      console.info('dataSizeCallback success');
      const jsonObj: ScannedInfos | null = JSON.parse(OnBackupSizeReport); // Parse the returned information and print it.
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
    bundleName: 'com.example.hiworld',
    lastIncrementalTime: 0 // The caller uses the last recorded incremental backup time. The value is 0 for a full backup.
  }];
  try {
    sessionBackup.getBackupDataSize(false, backupApps); // Obtain the size of data to be backed up for the applications specified in backupApps. false indicates using non-precise scanning.
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getBackupDataSize failed. Code: ${err.code}, message: ${err.message}`);
  }
  ```

**Example of the asynchronously returned JSON string:**

```json5
{
 "scanned": [ // Applications scanned in this round. Applications whose results have been returned will not be returned again in the next callback.
     {
         "name": "com.example.hiworld", // Application Name
         "dataSize": 1006060, // Data size
         "incDataSize":-1 // Incremental data size. The value is -1 for a full scan or non-precise scan, and the actual incremental data size for a precise incremental scan.
     },
     {
         "name": "com.example.myAPP",
         "dataSize": 5000027,
         "incDataSize": -1
     }
 ],
 "scanning": "com.example.smartAPP" // Application being scanned. This field is empty when the last result is returned.
}
```

### appendBundles

appendBundles(bundlesToBackup: string[], callback: AsyncCallback&lt;void&gt;): void

Adds applications to be backed up. In the entire current process, this method can be called only once after the SessionBackup instance is obtained. After the backup process ends, call release to release resources. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                      | Mandatory | Description                                                        |
| -------------- | ------------------------- | --------- | ------------------------------------------------------------------ |
| bundlesToBackup | string[]                  | Yes       | Array of application names to be backed up.                        |
| callback       | AsyncCallback&lt;void&gt; | Yes       | Callback invoked after the applications to be backed up are added asynchronously. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900020 | Invalid argument. |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.           |

**Example**

  ```ts
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

### appendBundles

appendBundles(bundlesToBackup: string[], infos?: string[]): Promise&lt;void&gt;

Adds the applications to be backed up. In the entire current process, this method can be called only once after an instance of the SessionBackup class is obtained. After the backup process is complete, call release to release resources. This API uses a promise to return the result asynchronously.

Since API version 12, the optional parameter infos is added, which can carry the extended information required by each application during backup. infos and bundlesToBackup correspond one-to-one by index.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name  | Type     | Mandatory | Description                       |
| --------------- | -------- | ---- | -------------------------- |
| bundlesToBackup | string[] | Yes   | Array of application names to be backed up. |
| infos           | string[] | No   | Array of extended information required by each application during backup, corresponding one-to-one with bundlesToBackup by index. The default value is empty. Supported since API version 12.|

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900020 | Invalid argument.        |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.           |

**Example**

  ```ts
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
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
  async function appendBundles() {
    try {
      let backupApps: Array<string> = [
        "com.example.hiworld",
        "com.example.myApp"
      ];
      await sessionBackup.appendBundles(backupApps);
      console.info('appendBundles success');
      // Carry extended parameters, where infos, details, and the outer type node are fixed nodes.
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

### release<sup>12+</sup>

release(): Promise&lt;void&gt;

After the backup process ends, the application disconnects from the service, causing the backup and restore service to exit. A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.                                                                                      |
| 13900001 | Operation not permitted.                                                                        |
| 13900005 | I/O error.                                                                                      |
| 13900042 | Unknown error.                                                                                  |

**Example**

  ```ts
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
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
  async function release() {
    try {
      await sessionBackup.release(); // Release the session after the backup task is complete.
      console.info('release success');
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`release failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

### cancel<sup>18+</sup>

cancel(bundleName: string): number

During a backup task, when the tool application detects data exceptions and needs to cancel the backup of an application, this API is called to terminate the backup task of that application. This API is called after the backup task of the corresponding application starts and before the task ends.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name for which the backup is to be canceled. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| number | Returns the cancellation status.<br/>0: The cancellation task is delivered successfully.<br/> 13500011: The task to be canceled has not started.<br/> 13500012: The task to be canceled does not exist.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        // Failed to transfer the file fd. Call the cancellation API to cancel the backup task of this application.
        let result = sessionBackup.cancel(file.bundleName);
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
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
  async function cancelTest() {
    let backupBundles: Array<string> = ['com.example.helloWorld'];
    try {
      await sessionBackup.appendBundles(backupBundles);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

### cleanBundleTempDir<sup>20+</sup>

cleanBundleTempDir(bundleName: string): Promise&lt;boolean&gt;

After a backup task ends, this API is provided for tools to clean up the temporary directory data of the current application (the backup and restore directories under the ./backup directory). A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name whose temporary directory data needs to be cleaned up. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;boolean&gt; | Promise object. Returning true indicates successful cleanup, and returning false indicates failed cleanup. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  async function cleanBundleTempDir(bundleName: string) {
    try {
      let res = await sessionBackup.cleanBundleTempDir(bundleName);
      if (res) {
        console.info(`cleanBundleTempDir succeeded.`);
      } else {
        console.error(`cleanBundleTempDir failed.`);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`cleanBundleTempDir failed. Code: ${err.code}, message: ${err.message}`);
    }
  }

  let generalCallbacks: backup.GeneralCallbacks = { // Define the general callbacks during the backup/restore process.
    // Callback for successful file sending.
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`onFileReady succeeded.`);
      fileIo.closeSync(file.fd);
    },
    // Callback for application backup/restore start.
    onBundleBegin: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`onBundleBegin succeeded.`);
    },
    // Callback for application backup/restore end. Call cleanBundleTempDir here for cleanup.
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
  let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
  ```

### getCompatibilityInfo<sup>20+</sup>

getCompatibilityInfo(bundleName: string, extInfo: string): Promise&lt;string&gt;

Obtains the application-defined capability description information in the backup service. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name whose capability information is to be queried. |
| extInfo | string | Yes | Extended information to be passed to the application. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;string&gt; | Promise object that returns the application-defined capability description information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { fileIo, backup } from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let generalCallbacks: backup.GeneralCallbacks = { // Define the general callbacks during the backup/restore process.
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

  async function getBackupCompatibilityInfo() {
    let sessionBackup = new backup.SessionBackup(generalCallbacks); // Create a backup process.
    let bundleName = "com.example.helloWorld";
    let extInfo = ""; // An empty value indicates that no additional information needs to be passed to the application.
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

## SessionRestore

Restore process object, used to support the application restore process. Before use, a SessionRestore instance must be created first.

### constructor

constructor(callbacks: GeneralCallbacks)

Constructor of the restore process, used to obtain an instance of the SessionRestore class.

The typical process is as follows: create a SessionRestore instance, call appendBundles to add the applications to be restored, obtain the file handle through getFileHandle and write the restore data, call publishFile to publish the file when necessary, and call release to release resources after the process ends.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                                  | Mandatory | Description                          |
| --------- | ------------------------------------- | --------- | ------------------------------------ |
| callbacks | [GeneralCallbacks](#generalcallbacks) | Yes       | Callbacks required by the restore process. |

**Example**

  ```ts
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create the restore process.
  ```

### getLocalCapabilities<sup>18+</sup>

getLocalCapabilities(): Promise&lt;FileData&gt;

Obtains a JSON file that describes local capabilities during a restore operation. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                                 | Description                            |
| ------------------------------------ | ------------------------------- |
| Promise&lt;[FileData](#filedata)&gt; | Promise object that returns a FileData object, which contains a file descriptor for reading the content of the local capability file. The file descriptor must be closed after use. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error.                                                    |
| 13900001 | Operation not permitted.                                      |
| 13900020 | Invalid argument.                                             |
| 13900042 | Internal error.                                                |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileIo, backup } from '@kit.CoreFileKit';

  interface LocalCapabilities { // Used to parse the capability file
    bundleInfos: BundleInfo[];
    deviceType: string;
    systemFullName: string;
  }

  interface BundleInfo { // Used to obtain the local capability information of a single application
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

  let generalCallbacks: backup.GeneralCallbacks = { // Defines the general callbacks during the backup/restore process
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
    let sessionRestore = new backup.SessionRestore(generalCallbacks); // Creates a restore process
    let basePath = '/data/storage/el2/base/backup';
    let path = basePath + '/localCapabilities.json'; // Local path for saving the capability file
    try {
      let fileData = await sessionRestore.getLocalCapabilities(); // Obtain the local capability file.
      if (fileData) {
        console.info('getLocalCapabilities success');
        console.info('fileData info:' + fileData.fd);
        if (!fileIo.accessSync(basePath)) {
          fileIo.mkdirSync(basePath);
          console.info('create success' + basePath);
        }
        fileIo.copyFileSync(fileData.fd, path); // Save the obtained local capability file to the local device.
        fileIo.closeSync(fileData.fd);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed with code: ${err.code}, message: ${err.message}`);
    }
    let data = fileIo.readTextSync(path, 'utf8'); // Obtain information from the local capability file.
    try {
      const jsonsObj: LocalCapabilities | null = JSON.parse(data); // Parse the local capability file and print part of the information.
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
      console.error(`parse failed with code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

**The capability file can be obtained through related APIs such as [fileIo.stat](js-apis-file-fs.md#fileiostat) provided by [@ohos.file.fs](js-apis-file-fs.md). The following is an example of the capability file content:**

 ```json
 {
  "backupVersion" : "16.0",
  "bundleInfos" :[{
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

### appendBundles

appendBundles(remoteCapabilitiesFd: number, bundlesToBackup: string[], callback: AsyncCallback&lt;void&gt;): void

Adds the applications to be restored. In the entire current process, this method can be called only once after the SessionRestore instance is obtained. After the restore process is complete, call release to release resources. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - During restoration, the service requires the capability file for related verification.
> - Therefore, remoteCapabilitiesFd can be obtained through the [getLocalCapabilities](#backupgetlocalcapabilities) API provided by the backup-side service, and its content can be modified based on the actual status of the applications to be restored. You can also generate the capability file by yourself based on the JSON example provided by getLocalCapabilities.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name           | Type                      | Mandatory | Description                                                        |
| ------------------- | ------------------------- | --------- | ------------------------------------------------------------------ |
| remoteCapabilitiesFd | number                    | Yes       | File descriptor of the capability file required for restoration.  |
| bundlesToBackup      | string[]                  | Yes       | Array of application names to be restored.                         |
| callback             | AsyncCallback&lt;void&gt; | Yes       | Callback invoked after the applications to be restored are added asynchronously. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.          |
| 13900020 | Invalid argument.        |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.           |

**Example**

  ```ts
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
  async function appendBundles() {
    let fileData : backup.FileData = {
      fd : -1
    }
    try {
      fileData = await backup.getLocalCapabilities();
      console.info('getLocalCapabilities success');
      let restoreApps: Array<string> = [
        "com.example.hiworld",
      ];
      sessionRestore.appendBundles(fileData.fd, restoreApps, (err: BusinessError) => {
        if (err) {
          console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('appendBundles success');
      });
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
    } finally {
      fileIo.closeSync(fileData.fd);
    }
  }
  ```

### appendBundles

appendBundles(remoteCapabilitiesFd: number, bundlesToBackup: string[], infos?: string[]): Promise&lt;void&gt;

Adds the applications to be restored. Starting from API version 12, the optional parameter infos is added, which can carry the information required for application restoration. infos and bundlesToBackup correspond one-to-one by index.

In the entire current process, this method can be called only once after an instance of the SessionRestore class is obtained. After the restore process ends, call release to release resources. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - The service requires its capability file for related verification during restoration.
> - Therefore, remoteCapabilitiesFd can be obtained through the [getLocalCapabilities](#backupgetlocalcapabilities) API provided by the backup-side service,
    and its content can be modified based on the actual status of the application to be restored. You can also generate a capability file by yourself based on the JSON example provided by getLocalCapabilities.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name            | Type     | Mandatory | Description                                                        |
| -------------------- | -------- | --------- | ------------------------------------------------------------------ |
| remoteCapabilitiesFd | number   | Yes       | File descriptor of the capability file required for restoration.   |
| bundlesToBackup      | string[] | Yes       | Array of package names of the applications to be restored.         |
| infos<sup>12+</sup>  | string[] | No        | Array of extended information required by each application during restoration, corresponding one-to-one with bundlesToBackup by index. The default value is empty. Supported since API version 12. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900005 | I/O error.               |
| 13900011 | Out of memory.           |
| 13900020 | Invalid argument.        |
| 13900025 | No space left on device. |
| 13900042 | Unknown error.           |

**Example**

  ```ts
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
  async function appendBundles() {
    let fileData : backup.FileData = {
      fd : -1
    }
    try {
      fileData = await backup.getLocalCapabilities();
      console.info('getLocalCapabilities success');
      let restoreApps: Array<string> = [
        "com.example.hiworld",
      ];
      await sessionRestore.appendBundles(fileData.fd, restoreApps);
      console.info('appendBundles success');
      // Call with extended parameters.
      let infos: Array<string> = [
        `
         {
          "infos":[
            {
              "details": [
                {
                  "detail": [
                    {
                      "source": "com.example.hiworld", // Old system package name of the application.
                      "target": "com.example.helloworld" // New system package name of the application
                    }
                  ],
                  "type": "app_mapping_relation"
                }
              ],
              "type":"broadcast"
            }
          ]
         }
        `
      ]
      await sessionRestore.appendBundles(fileData.fd, restoreApps, infos);
      console.info('appendBundles success');
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
    } finally {
      fileIo.closeSync(fileData.fd);
    }
  }
  ```

### getFileHandle

getFileHandle(fileMeta: FileMeta, callback: AsyncCallback&lt;void&gt;): void

Requests to obtain a shared file from the service. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - This API is part of the zero-copy feature (which reduces unnecessary memory copies and enables more efficient transfer). The server shares the file to be restored through a file descriptor. After the client obtains the file handle through onFileReady, it can use APIs such as [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile) to copy data directly between file descriptors, avoiding reading data into application memory before writing it out.
> - Before using getFileHandle, you need to obtain an instance of the SessionRestore class and successfully add the applications to be restored through appendBundles.
> - Developers can obtain the file handle through the onFileReady callback. When the client finishes file operations, it needs to use publishFile to publish the file.
> - getFileHandle can be called multiple times based on the number of files to be restored.
> - The files to be restored do not support relative paths (../) or symbolic links.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                      | Mandatory | Description                             |
| --------- | ------------------------- | --------- | --------------------------------------- |
| fileMeta  | [FileMeta](#filemeta)     | Yes       | Metadata of the file to be restored.    |
| callback  | AsyncCallback&lt;void&gt; | Yes       | Callback invoked after the file handle is asynchronously requested. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900020 | Invalid argument.        |
| 13900042 | Unknown error.           |

**Example**

  ```ts
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
  let fileMeta: backup.FileMeta = {
    bundleName: 'com.example.hiworld',
    uri: "test.txt"
  }
  sessionRestore.getFileHandle(fileMeta, (err: BusinessError) => {
    if (err) {
      console.error(`getFileHandle failed. Code: ${err.code}, message: ${err.message}`);
    }
    console.info('getFileHandle success');
  });
  ```

### getFileHandle

getFileHandle(fileMeta: FileMeta): Promise&lt;void&gt;

Requests to obtain a shared file from the service. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - This API is part of the zero-copy feature (which reduces unnecessary memory copies and achieves more efficient transmission). The server shares the file to be restored through a file descriptor. After the client obtains the file handle through onFileReady, it can use APIs such as [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile) to directly copy data between file descriptors, avoiding reading data into application memory before writing it out.
> - Before using getFileHandle, you need to obtain an instance of the SessionRestore class and successfully add the applications to be restored through appendBundles.
> - Developers can obtain the file handle through the onFileReady callback. When the client completes file operations, publishFile must be used for publishing.
> - getFileHandle can be called multiple times based on the number of files to be restored.
> - Relative paths (../) and symbolic links are not supported for the files to be restored.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                  | Mandatory | Description                          |
| --------- | --------------------- | --------- | ------------------------------------ |
| fileMeta  | [FileMeta](#filemeta) | Yes       | Metadata of the file to be restored. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.              |
| 13900001 | Operation not permitted. |
| 13900020 | Invalid argument.        |
| 13900042 | Unknown error.          |

**Example**

  ```ts
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
  async function getFileHandle() {
    try {
      let fileMeta: backup.FileMeta = {
        bundleName: 'com.example.hiworld',
        uri: "test.txt"
      }
      await sessionRestore.getFileHandle(fileMeta);
      console.info('getFileHandle success');
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getFileHandle failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

### publishFile

publishFile(fileMeta: FileMeta, callback: AsyncCallback&lt;void&gt;): void

Publishes FileMeta to the backup service so that the service knows the file content is ready. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - This API is part of the zero-copy feature (which reduces unnecessary memory copies and achieves more efficient transmission). For zero-copy methods, refer to the zero-copy APIs such as [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile) provided by [@ohos.file.fs](js-apis-file-fs.md).
> - After the server returns a file handle through onFileReady, the client can use zero-copy operations to copy the corresponding file content to the file handle provided by the server.
> - This API can be called only after the caller completes writing all data to be restored, and the caller must ensure the consistency and integrity of the data to be restored.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                      | Mandatory | Description                         |
| --------- | ------------------------- | --------- | ----------------------------------- |
| fileMeta  | [FileMeta](#filemeta)     | Yes       | Metadata of the file to restore.    |
| callback  | AsyncCallback&lt;void&gt; | Yes       | Callback invoked after the file is published asynchronously. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900020 | Invalid argument.        |
| 13900042 | Unknown error.           |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let g_session: backup.SessionRestore;
  let initMap = new Map<string, number>();
  let testFileNum = 123; // 123: Example of the number of files required for restoration.
  let testBundleName = 'com.example.myapplication'; // Test bundle name.
  initMap.set(testBundleName, testFileNum);
  let countMap = new Map<string, number>();
  countMap.set(testBundleName, 0); // Initialize the number of files actually written.
  function createSessionRestore() {
    let generalCallbacks: backup.GeneralCallbacks = {
      onFileReady: (err: BusinessError, file: backup.File) => {
        if (err) {
          console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('onFileReady success');
        fileIo.closeSync(file.fd);
        let cnt = countMap.get(file.bundleName) || 0;
        countMap.set(file.bundleName, cnt + 1); // Update the number of files actually written.
        // Call this when the number of files to restore equals the number of files actually written, to ensure data consistency and integrity.
        if (countMap.get(file.bundleName) == initMap.get(file.bundleName)) { // Trigger publishFile after all files of each bundle are received.
          let fileMeta: backup.FileMeta = {
            bundleName: file.bundleName,
            uri: ''
          }
          g_session.publishFile(fileMeta, (err: BusinessError) => {
            if (err) {
              console.error(`publishFile failed. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('publishFile success');
          });
        }
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
    let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
    return sessionRestore;
  }
  g_session = createSessionRestore();
  ```

### publishFile

publishFile(fileMeta: FileMeta): Promise&lt;void&gt;

Publishes FileMeta to the backup service so that the service knows the file content is ready. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - This API is part of the zero-copy feature (which reduces unnecessary memory copies and achieves more efficient transfer). For zero-copy methods, refer to the zero-copy APIs such as [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile) provided by [@ohos.file.fs](js-apis-file-fs.md).
> - After the server returns a file handle through onFileReady, the client can copy the corresponding file content to the file handle provided by the server through zero-copy operations.
> - This API can be called only after the caller has completed writing all data to be restored, and the caller must ensure the consistency and integrity of the data to be written for restoration.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                  | Mandatory | Description                    |
| --------- | --------------------- | --------- | ------------------------------ |
| fileMeta  | [FileMeta](#filemeta) | Yes       | Metadata of the restore file. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted. |
| 13900020 | Invalid argument.        |
| 13900042 | Unknown error.           |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let g_session: backup.SessionRestore;
  let initMap = new Map<string, number>();
  let testFileNum = 123; // 123: Example of the number of files required for restoration.
  let testBundleName = 'com.example.myapplication'; // Test bundle name.
  initMap.set(testBundleName, testFileNum);
  let countMap = new Map<string, number>();
  countMap.set(testBundleName, 0); // Initialize the number of files actually written.
  async function publishFile(file: backup.FileMeta) {
    let fileMeta: backup.FileMeta = {
      bundleName: file.bundleName,
      uri: ''
    }
    await g_session.publishFile(fileMeta);
  }
  function createSessionRestore() {
    let generalCallbacks: backup.GeneralCallbacks = {
      onFileReady: (err: BusinessError, file: backup.File) => {
        if (err) {
          console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('onFileReady success');
        fileIo.closeSync(file.fd);
        let cnt = countMap.get(file.bundleName) || 0;
        countMap.set(file.bundleName, cnt + 1); // Update the number of files actually written.
        // Called when the number of files required for restoration equals the number of files actually written, to ensure data consistency and integrity.
        if (countMap.get(file.bundleName) == initMap.get(file.bundleName)) { // Trigger publishFile after all files of each bundle are received.
          publishFile(file);
        }
        console.info('publishFile success');
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
    let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
    return sessionRestore;
  }
  g_session = createSessionRestore();
  ```

### release<sup>12+</sup>

release(): Promise&lt;void&gt;

After the restore process ends, the application disconnects from the service so that the backup and restore service exits. A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.                                                                                      |
| 13900001 | Operation not permitted.                                                                        |
| 13900005 | I/O error.                                                                                      |
| 13900042 | Unknown error.                                                                                  |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let g_session: backup.SessionRestore;
  let initMap = new Map<string, number>();
  let testFileNum = 123; // 123: Example of the number of files required for restore.
  let testBundleName = 'com.example.myapplication'; // Test bundle name.
  initMap.set(testBundleName, testFileNum);
  let countMap = new Map<string, number>();
  countMap.set(testBundleName, 0); // Initialize the number of files actually written.
  function createSessionRestore() {
    let generalCallbacks: backup.GeneralCallbacks = {
      onFileReady: (err: BusinessError, file: backup.File) => {
        if (err) {
          console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('onFileReady success');
        fileIo.closeSync(file.fd);
        let cnt = countMap.get(file.bundleName) || 0;
        countMap.set(file.bundleName, cnt + 1); // Update the number of files actually written.
        // Called when the number of files required for restore equals the number of files actually written, to ensure data consistency and integrity.
        if (countMap.get(file.bundleName) == initMap.get(file.bundleName)) { // Trigger publishFile after all files of each bundle are received.
          let fileMeta: backup.FileMeta = {
            bundleName: file.bundleName,
            uri: ''
          }
          g_session.publishFile(fileMeta, (err: BusinessError) => {
            if (err) {
              console.error(`publishFile failed. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('publishFile success');
          });
        }
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
    let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create the restore process.
    return sessionRestore;
  }
  g_session = createSessionRestore();
  async function releaseSession() {
    try {
      await g_session.release();
      console.info('release success');
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`release failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

### cancel<sup>18+</sup>

cancel(bundleName: string): number

During the restore process, when the tool application detects abnormal data and needs to cancel the restore of an application, it calls this API to terminate the restore task of that application. This API is called after the restore task of the corresponding application starts and before the task ends.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name          | Type     | Mandatory | Description                       |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes   | Name of the application whose restore is to be canceled. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| number | Returns the cancellation status.<br/>0: The cancellation task is delivered successfully.<br/> 13500011: The task to be canceled has not started.<br/> 13500012: The task to be canceled does not exist.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        // If the file FD transfer fails, call the cancellation API to cancel the restore task of this application.
        let result = sessionRestore.cancel(file.bundleName);
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
  async function cancelTest() {
    let fileData: backup.FileData = {
      fd: -1
    }
    fileData = await backup.getLocalCapabilities(); // Obtain the capability set file through the getLocalCapabilities API provided by the backup/restore framework.
    let backupBundles: Array<string> = ['com.example.helloWorld'];
    try {
      await sessionRestore.appendBundles(fileData.fd, backupBundles);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
    } finally {
      fileIo.closeSync(fileData.fd);
    }
  }
  ```

### cleanBundleTempDir<sup>20+</sup>

cleanBundleTempDir(bundleName: string): Promise&lt;boolean&gt;

After a restore task ends, this API is provided for tools to clean up the temporary directory data of the current application (the backup and restore directories under the ./backup directory). A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name whose temporary directory data needs to be cleaned up. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;boolean&gt; | Promise object. Returns true if the cleanup succeeds and false if the cleanup fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  async function cleanBundleTempDir(bundleName: string) {
    try {
      let res = await sessionRestore.cleanBundleTempDir(bundleName);
      if (res) {
        console.info(`cleanBundleTempDir succeeded.`);
      } else {
        console.error(`cleanBundleTempDir failed.`);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`cleanBundleTempDir failed. Code: ${err.code}, message: ${err.message}`);
    }
  }

  let generalCallbacks: backup.GeneralCallbacks = { // Define the general callbacks during the backup/restore process.
    // Callback for successful file sending.
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`onFileReady succeeded.`);
      fileIo.closeSync(file.fd);
    },
    // Callback for the start of application backup/restore.
    onBundleBegin: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`onBundleBegin succeeded.`);
    },
    // Callback for the end of application backup/restore. Call cleanBundleTempDir here for cleanup.
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
  let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create the restore process.
  ```

### getCompatibilityInfo<sup>20+</sup>

getCompatibilityInfo(bundleName: string, extInfo: string): Promise&lt;string&gt;

Obtains the application-defined capability description information during the restore process. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name for which the capability information is to be queried. |
| extInfo | string | Yes | Extended information to be passed to the application. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;string&gt; | Promise object that returns the application-defined capability description information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { fileIo, backup } from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let generalCallbacks: backup.GeneralCallbacks = { // Define the general callbacks during the backup/restore process.
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

  async function getRestoreCompatibilityInfo() {
    let sessionRestore = new backup.SessionRestore(generalCallbacks); // Create a restore process.
    let bundleName = "com.example.helloWorld";
    let extInfo = ""; // An empty string indicates that no additional information needs to be passed to the application.
    try {
      let retInfo = await sessionRestore.getCompatibilityInfo(bundleName, extInfo);
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

### migrateFile

migrateFile(pathInfo: PathInfo, fileMeta: FileMeta): Promise&lt;void&gt;

Used to migrate a file from the source path to the target path. Before using this API, you need to obtain a SessionRestore instance and successfully add the application to be restored through appendBundles. This API is used in scenarios where the file path needs to be adjusted, the storage location needs to be migrated, or data upgrade migration needs to be processed during the restore process. The execution result is returned through the onMigrateResult callback. A Promise is used for asynchronous callback.

**Since:** 26.0.0

**Required permissions**: ohos.permission.BACKUP

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ------------------------------- |
| pathInfo | [PathInfo](#pathinfo) | Yes | Path information, including the source path and target path. For path length limits and restrictions on relative paths and symbolic links, see [PathInfo](#pathinfo). |
| fileMeta | [FileMeta](#filemeta) | Yes | File metadata, including bundleName and uri. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted.               |
| 13900020 | Invalid argument. |

**Example**

```ts
import { backup } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
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
    console.info(`onAllBundlesEnd succeeded.`);
  },
  onBackupServiceDied: () => {
    console.info(`service died.`);
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport succeeded, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess succeeded, bundleName: ${bundleName}, process: ${process}`);
  },
  onMigrateResult: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onMigrateResult failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onMigrateResult succeeded, bundleName: ' + bundleName);
  }
};

async function testMigrateFile() {
  let sessionRestore = new backup.SessionRestore(generalCallbacks);
  try {
    await sessionRestore.migrateFile(
      {
        srcPath: "/data/storage/el1/base/files/",
        destPath: "/data/storage/el2/base/files/"
      },
      {
        bundleName: 'com.example.app',
        uri: "" // Set uri to empty when migrating files by directory.
      }
    );
    console.info("migrateFile succeeded.");
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`migrateFile failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### getApkFileHandle

getApkFileHandle(path: string, fileName: string): Promise&lt;FileData&gt;

Obtains the file handle of an APK file during the restore process. Before using this API, you must obtain a SessionRestore instance and successfully add the application to be restored through appendBundles. The returned FileData must be closed after use. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.BACKUP

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ---------- | ------ | ---- | ------------------------------- |
| path | string | Yes | Path of the APK file. The total length of the path concatenated with fileName is limited to 4096 characters. Relative paths and symbolic links are not supported. If the length limit is exceeded, a parameter error is returned. |
| fileName | string | Yes | Name of the APK file. The total length of the name concatenated with path is limited to 4096 characters. Relative paths and symbolic links are not supported. If the length limit is exceeded, a parameter error is returned. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;[FileData](#filedata)&gt; | Promise object that returns a FileData object, which contains the file descriptor and file attributes. The returned file is a temporary file and is automatically deleted when closed. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error.               |
| 13900001 | Operation not permitted.               |
| 13900020 | Invalid argument. |

**Example**

```ts
import { backup } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let generalCallbacks: backup.GeneralCallbacks = {
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
    console.info(`onAllBundlesEnd succeeded.`);
  },
  onBackupServiceDied: () => {
    console.info(`service died`);
  },
  onResultReport: (bundleName: string, result: string) => {
    console.info(`onResultReport succeeded, bundleName: ${bundleName}, result: ${result}`);
  },
  onProcess: (bundleName: string, process: string) => {
    console.info(`onProcess succeeded, bundleName: ${bundleName}, process: ${process}`);
  },
  onMigrateResult: (err: BusinessError, bundleName: string) => {
    if (err) {
      console.error(`onMigrateResult failed. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('onMigrateResult succeeded, bundleName: ' + bundleName);
  }
};

async function testGetApkFileHandle() {
  let sessionRestore = new backup.SessionRestore(generalCallbacks);
  try {
    let fileData: backup.FileData = await sessionRestore.getApkFileHandle("/data/storage/el1/base/files", "app.apk");
    console.info("getApkFileHandle succeeded, fd: " + fileData.fd);
    // Close the file descriptor after use.
    fileIo.closeSync(fileData.fd);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getApkFileHandle failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### getFileHandles

getFileHandles(fileMeta: FileMeta): Promise&lt;void&gt;

Obtains the handle of a shared file from the service. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - This API is part of the zero-copy feature, which reduces unnecessary memory copies and improves transmission efficiency. For details about the zero-copy method, see the zero-copy APIs provided by [@ohos.file.fs](js-apis-file-fs.md), such as [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile).
> - Before using [getFileHandles](#getfilehandles), obtain a [SessionRestore](#sessionrestore) instance and add the applications whose data is to be restored by calling [appendBundles](#appendbundles-2).
> - File handles can be obtained through [OnFileReadyBatch](#onfilereadybatch). After the client finishes file operations, use [publishFile](#publishfile) to publish the file.
> - The getFileHandles API can be called multiple times based on the number of files to be restored.
> - The file to be restored cannot be a relative path (../) or a symbolic link.

**Since:** 26.0.0

**Required permissions**: ohos.permission.BACKUP

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**System API**: This is a system API.

**Parameters**

| Name | Type                  | Mandatory | Description               |
| --------- | --------------------- | --------- | ------------------------- |
| fileMeta  | [FileMeta](#filemeta) | Yes       | Metadata of the file to be sent. The file must come from the backup process or the [getLocalCapabilities](#getlocalcapabilities18-1) method. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                |
| -------- | ----------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error.              |
| 13900001 | Operation not permitted. |
| 13900020 | Invalid argument.        |

**Example**

  ```ts
  import { fileIo, backup } from '@kit.CoreFileKit';
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
    onFileReadyBatch: (error: BusinessError<void>, files: Array<backup.File>): void => {
      if (error) {
        console.error(`onFileReadyBatch failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      for (let file of files) {
        console.info(`onFileReadyBatch success with file: ${file.bundleName}, ${file.uri}`);
        fileIo.closeSync(file.fd);
      }
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
  // Create a restore process instance.
  let sessionRestore = new backup.SessionRestore(generalCallbacks);
  async function getFileHandles() {
    let testArray: string[] = ["test1", "test2"];
    try {
      let fileMeta: backup.FileMeta = {
        bundleName: "com.example.hiworld",
        uri: "test.txt",
        uris: testArray
      };
      await sessionRestore.getFileHandles(fileMeta);
      console.info('getFileHandles success');
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getFileHandles failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

## IncrementalBackupSession<sup>12+</sup>

An incremental backup process object used to support the application incremental backup process. Before use, an IncrementalBackupSession instance must be created first. This process identifies changed data based on the last incremental backup time and the manifest file, and is suitable for backing up application incremental data.

### constructor<sup>12+</sup>

constructor(callbacks: GeneralCallbacks)

Constructor of the incremental backup process, used to obtain an instance of the IncrementalBackupSession class. The typical process is as follows: create an IncrementalBackupSession instance, call appendBundles to add the applications to be incrementally backed up, wait for the callback to return the incremental backup result, and call release to release resources after the process ends.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type                                  | Mandatory | Description                              |
| --------- | ------------------------------------- | --------- | ---------------------------------------- |
| callbacks | [GeneralCallbacks](#generalcallbacks) | Yes       | Callbacks required by the incremental backup process. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create the incremental backup process
  ```

### getLocalCapabilities<sup>18+</sup>

getLocalCapabilities(): Promise&lt;FileData&gt;

Obtains a JSON file that describes local capabilities in the incremental backup service. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                                 | Description                            |
| ------------------------------------ | ------------------------------- |
| Promise&lt;[FileData](#filedata)&gt; | Promise object that returns a FileData object, which contains a file descriptor for reading the content of the local capability file. The file descriptor must be closed after use. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error.                                                    |
| 13900001 | Operation not permitted.                                      |
| 13900020 | Invalid argument.                                             |
| 13900042 | Internal error.                                                |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  interface LocalCapabilities { // Used to parse the capability file
    bundleInfos: BundleInfo[];
    deviceType: string;
    systemFullName: string;
  }

  interface BundleInfo { // Used to obtain the local capability information of a single application
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

  let generalCallbacks: backup.GeneralCallbacks = { // Defines the general callbacks during the backup/restore process
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
    let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Creates an incremental backup process
    let basePath = '/data/storage/el2/base/backup';
    let path = basePath + '/localCapabilities.json'; // Path for saving the capability file locally
    try {
      let fileData = await incrementalBackupSession.getLocalCapabilities(); // Obtain the local capability file.
      if (fileData) {
        console.info('getLocalCapabilities success');
        console.info('fileData info:' + fileData.fd);
        if (!fileIo.accessSync(basePath)) {
          fileIo.mkdirSync(basePath);
          console.info('create success' + basePath);
        }
        fileIo.copyFileSync(fileData.fd, path); // Save the obtained local capability file locally.
        fileIo.closeSync(fileData.fd);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getLocalCapabilities failed. Code: ${err.code}, message: ${err.message}`);
    }
    let data = fileIo.readTextSync(path, 'utf8'); // Obtain information from the local capability file.
    try {
      const jsonsObj: LocalCapabilities | null = JSON.parse(data); // Parse the local capability file and print partial information.
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

**The capability file can be obtained through related APIs such as [fileIo.stat](js-apis-file-fs.md#fileiostat) provided by [@ohos.file.fs](js-apis-file-fs.md). An example of the capability file content is as follows:**

 ```json
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

### getBackupDataSize<sup>18+</sup>

getBackupDataSize(isPreciseScan: boolean, dataList: Array\<IncrementalBackupTime\>): Promise&lt;void&gt;

Obtains the amount of data to be backed up for an application. This method is called before appendBundles. It is used together with onBackupSizeReport, and the scan result is returned through the onBackupSizeReport callback. A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name    | Type                                                     | Mandatory | Description                                                         |
| ------------- | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| isPreciseScan | boolean                                                  | Yes  | Whether to perform a precise scan. The value true indicates a precise scan, and false indicates a non-precise scan. A non-precise scan is fast and returns an estimated data size. A precise scan is slow but returns a more accurate result. However, because the data to be backed up may change during the actual backup process, the precise scan result is not guaranteed to exactly match the actual amount of backup data. |
| dataList      | Array<[IncrementalBackupTime](#incrementalbackuptime12)> | Yes  | List of applications to be backed up, used to describe the applications whose data size is to be obtained and the time of the last backup (enter 0 for a full backup). |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 13600001 | IPC error.                                                    |
| 13900001 | Operation not permitted.                                      |
| 13900020 | Invalid argument.                                             |
| 13900042 | Internal error.                                                |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  interface ScannedInfos { // Used to parse the scan result.
    scanned: [];
    scanning: string;
  }

  interface ScannedInfo { // Used to parse the scan result of a single application.
    bundleName: string;
    dataSize: number;
    incDataSize: number;
  }

  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => { // Define the common callbacks used during the backup/restore process.
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
    // The callback function is used together with getBackupDataSize to return the obtained data size of an application and the bundle name of the application whose data size is being obtained.
    // onBackupSizeReport in generalCallbacks returns the scan result every 5 seconds (or immediately if the scan is completed within 5 seconds) until the data sizes of all applications in dataList are returned.
    onBackupSizeReport: (OnBackupSizeReport) => {
      console.info('dataSizeCallback success');
      const jsonObj: ScannedInfos | null = JSON.parse(OnBackupSizeReport); // Parse the returned information and print it.
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

  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process.

  let backupApps: backup.IncrementalBackupTime[] = [{
    bundleName: 'com.example.hiworld',
    lastIncrementalTime: 1700107870 // The caller records the last incremental backup time.
  }];
  try {
    incrementalBackupSession.getBackupDataSize(true, backupApps); // Obtain the size of data to be backed up for the specified applications in backupApps. true indicates using precise scanning.
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`getBackupDataSize failed. Code: ${err.code}, message: ${err.message}`);
  }
  ```

**Example of the asynchronously returned JSON string:**

```json5
{
 "scanned": [ // Applications whose scanning is completed this time. Applications whose results have been returned will not be returned again in the next callback.
     {
         "name": "com.example.hiworld", // Application name
         "dataSize": 1006060, // Data size
         "incDataSize": 50800 // Incremental data size
     },
     {
         "name": "com.example.myAPP",
         "dataSize": 5000027,
         "incDataSize": 232344
     }
 ],
 "scanning" :"com.example.smartAPP" // Application being scanned. This field is empty when the last result is returned.
}
```

### appendBundles<sup>12+</sup>

appendBundles(bundlesToBackup: Array&lt;IncrementalBackupData&gt;): Promise&lt;void&gt;

Adds applications that require incremental backup. In the current entire process, appendBundles can be called at any time before the release API is triggered. A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name  | Type                                                           | Mandatory | Description                                      |
| --------------- | -------------------------------------------------------------- | --------- | ------------------------------------------------ |
| bundlesToBackup | Array&lt;[IncrementalBackupData](#incrementalbackupdata12)&gt; | Yes       | Array of applications that require incremental backup. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.                                                                                      |
| 13900001 | Operation not permitted.                                                                        |
| 13900005 | I/O error.                                                                                      |
| 13900011 | Out of memory.                                                                                  |
| 13900025 | No space left on device.                                                                        |
| 13900042 | Unknown error.                                                                                  |

**Example**

  ```ts
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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process.
  let incrementalBackupData: backup.IncrementalBackupData = {
    bundleName: 'com.example.hiworld',
    lastIncrementalTime: 1700107870, // The caller passes the timestamp of the last backup.
    manifestFd: fileIo.openSync('/data/storage/el2/base/backup/manifest.json').fd // The caller passes the manifest file handle of the last backup.
  }
  let incrementalBackupDataArray: backup.IncrementalBackupData[] = [incrementalBackupData];
  incrementalBackupSession.appendBundles(incrementalBackupDataArray).then(() => {
    console.info('appendBundles success');
  }).catch((err: BusinessError) => {
    console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
  }); // Add applications that require incremental backup.
  ```

### appendBundles<sup>12+</sup>

appendBundles(bundlesToAppend: Array&lt;IncrementalBackupData&gt;, infos: string[]): Promise&lt;void&gt;

Adds applications that require incremental backup. In the current entire process, appendBundles can be called at any time before the release API is triggered. A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name  | Type                                                           | Mandatory | Description                       |
| --------------- | -------------------------------------------------------------- | ---- | -------------------------- |
| bundlesToAppend | Array&lt;[IncrementalBackupData](#incrementalbackupdata12)&gt; | Yes   | Array of applications that require incremental backup. |
| infos  | string[] | Yes   | Array of extended information required by each application during backup, corresponding to bundlesToAppend by index. Supported since API version 12. |

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.                                                                                      |
| 13900001 | Operation not permitted.                                                                        |
| 13900005 | I/O error.                                                                                      |
| 13900011 | Out of memory.                                                                                  |
| 13900025 | No space left on device.                                                                        |
| 13900042 | Unknown error.                                                                                  |

**Example**

  ```ts
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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process.
  let incrementalBackupData: backup.IncrementalBackupData = {
    bundleName: 'com.example.hiworld',
    lastIncrementalTime: 1700107870, // Timestamp of the last backup passed by the caller.
    manifestFd: fileIo.openSync('/data/storage/el2/base/backup/manifest.json').fd // Manifest file handle of the last backup passed by the caller.
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
  // Add applications that require incremental backup.
  incrementalBackupSession.appendBundles(incrementalBackupDataArray, infos).then(() => {
    console.info('appendBundles success');
  }).catch((err: BusinessError) => {
    console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
  }); 
  ```

### release<sup>12+</sup>

release(): Promise&lt;void&gt;

Ends the incremental backup process. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Return value**

| Type                | Description                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|
| 13600001 | IPC error.                                                                                      |
| 13900001 | Operation not permitted.                                                                        |
| 13900005 | I/O error.                                                                                      |
| 13900042 | Unknown error.                                                                                  |

**Example**

  ```ts
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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process.
  async function release() {
    try {
      await incrementalBackupSession.release(); // End the incremental backup process.
      console.info('release success');
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`release failed. Code: ${err.code}, message: ${err.message}`);
    }
  }
  ```

### cancel<sup>18+</sup>

cancel(bundleName: string): number

During an incremental backup task, when the tool application detects data anomalies and needs to cancel the incremental backup of a specific application, it calls this API to terminate the incremental backup task of that application. This API is called after the incremental backup task of the corresponding application starts and before the task ends.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name for which the incremental backup is to be canceled. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| number | Returns the cancellation status.<br/>0: The cancellation task is delivered successfully, <br/> 13500011: The task to be canceled has not started, <br/> 13500012: The task to be canceled does not exist.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.|

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let generalCallbacks: backup.GeneralCallbacks = {
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        // File fd transfer failed. Call the cancel API to cancel the incremental backup task of this application.
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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process.
  let backupBundles: Array<backup.IncrementalBackupData> = [];
  let bundleData: backup.IncrementalBackupData = {
    bundleName: 'com.example.helloWorld',
    lastIncrementalTime: 1700107870, // The caller passes the timestamp of the last backup.
    manifestFd: fileIo.openSync('/data/storage/el2/base/backup/manifest.json').fd // The caller passes the manifest file handle of the last backup.
  }
  backupBundles.push(bundleData);
  incrementalBackupSession.appendBundles(backupBundles).then(() => {
    console.info('appendBundles success');
  }).catch((err: BusinessError) => {
    console.error(`appendBundles failed. Code: ${err.code}, message: ${err.message}`);
  });

  ```

### cleanBundleTempDir<sup>20+</sup>

cleanBundleTempDir(bundleName: string): Promise&lt;boolean&gt;

After an incremental backup task ends, this API is provided for tools to clean up the temporary directory data of the current application (the backup and restore directories under the ./backup directory). A Promise is used to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name whose temporary directory data needs to be cleaned up. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;boolean&gt; | Promise object. The value **true** indicates that the cleanup is successful, and **false** indicates that the cleanup fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { fileIo, backup} from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  async function cleanBundleTempDir(bundleName: string) {
    try {
      let res = await incrementalBackupSession.cleanBundleTempDir(bundleName);
      if (res) {
        console.info(`cleanBundleTempDir succeeded.`);
      } else {
        console.error(`cleanBundleTempDir failed.`);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`cleanBundleTempDir failed. Code: ${err.code}, message: ${err.message}`);
    }
  }

  let generalCallbacks: backup.GeneralCallbacks = { // Define the general callbacks during backup/restore.
    // Callback for successful file sending.
    onFileReady: (err: BusinessError, file: backup.File) => {
      if (err) {
        console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`onFileReady succeeded.`);
      fileIo.closeSync(file.fd);
    },
    // Callback for the start of application backup/restore.
    onBundleBegin: (err: BusinessError, bundleName: string) => {
      if (err) {
        console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`onBundleBegin succeeded.`);
    },
    // Callback for the end of application backup/restore. Call cleanBundleTempDir here for cleanup.
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
  let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process.
  ```

### getCompatibilityInfo<sup>20+</sup>

getCompatibilityInfo(bundleName: string, extInfo: string): Promise&lt;string&gt;

Obtains the application-defined capability description information in the incremental backup service. This API uses a promise to return the result asynchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.BACKUP

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | -------- | ---- | -------------------------- |
| bundleName | string | Yes | Application name for which the capability information is to be queried. |
| extInfo | string | Yes | Extended information to be passed to the application. |

**Return value**

| Type | Description |
| ------------------- | ----------------------- |
| Promise&lt;string&gt; | Promise object that returns the application-defined capability description information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.              |
| 202      | Permission verification failed, application which is not a system application uses system API. |

**Example**

  ```ts
  import { fileIo, backup } from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let generalCallbacks: backup.GeneralCallbacks = { // Define the general callbacks during the backup/restore process
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
    let incrementalBackupSession = new backup.IncrementalBackupSession(generalCallbacks); // Create an incremental backup process
    let bundleName = "com.example.helloWorld";
    let extInfo = ""; // Empty indicates that no additional information needs to be passed to the application
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
