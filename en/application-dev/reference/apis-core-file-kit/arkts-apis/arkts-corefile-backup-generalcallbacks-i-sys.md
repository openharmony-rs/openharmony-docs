# GeneralCallbacks (System API)

General callbacks for both backup and restore procedure. The backup service will notify the client by these callbacks.

@interface GeneralCallbacks

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## onBackupSizeReport

```TypeScript
onBackupSizeReport?: OnBackupSizeReport
```

Callback called when the backup_sa service return result information. The first return string parameter indicates the result of the scanned bundle datasize.

**Since:** 18

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## onFileReadyBatch

```TypeScript
onFileReadyBatch?: OnFileReadyBatch
```

Callback called when the backup service tries to send files to the client. The File argument indicates a file to send to the client. The returned file is owned by the backup service and will be cleaned by the service once the file is closed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |

## onProcess

```TypeScript
onProcess(bundleName: string, process: string): void
```

Callback called when the backup_sa service return result information. The first return string parameter indicates the result of the bundle.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | the bundleName that triggers the callback. |
| process | string | Yes | the process info of the bundle. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 13500006 | Tar error |
| 13500008 | Untar error |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |

**Examples**

```TypeScript
import { backup } from '@kit.CoreFileKit';

onProcess: (bundleName: string, process: string) => {
  console.info('onProcess bundleName : ' + bundleName);
  console.info('onProcess processInfo : ' + process);
}
```

## onResultReport

```TypeScript
onResultReport(bundleName: string, result: string): void
```

Callback called when the backup service return result information. The first return string parameter indicates the bundleName that triggers the callback. The second return string parameter indicates the result of the bundle.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | the bundleName that triggers the callback. |
| result | string | Yes | the result of the bundle. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { backup } from '@kit.CoreFileKit';

onResultReport: (bundleName: string, result: string) => {
  console.info('onResultReport bundleName : ' + bundleName);
  console.info('onResultReport result : ' + result);
}
```

## onAllBundlesEnd

```TypeScript
onAllBundlesEnd: AsyncCallback<undefined>
```

Callback called when the all the bundles to backup/restore are done or aborted unexpectedly.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;undefined&gt;

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

onAllBundlesEnd: (err: BusinessError) => {
  if (err) {
    console.error(`onAllBundlesEnd failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('onAllBundlesEnd success');
}
```

## onBackupServiceDied

```TypeScript
onBackupServiceDied: Callback<undefined>
```

Callback called when the backup service dies unexpectedly.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;undefined&gt;

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Examples**

```TypeScript
onBackupServiceDied: () => {
  console.info('onBackupServiceDied success');
}
```

## onBundleBegin

```TypeScript
onBundleBegin: AsyncCallback<string, void | string>
```

Callback called when a backup/restore procedure for an bundle is started. The first return string parameter indicates the name of the bundle. The second return string parameter indicates that when BusinessError errors occur, the callback data is the name of the bundle.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string, void &#124; string&gt;

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 13500001 | The application is not added to the backup or restore |
| 13500002 | Failed to start application extension Procedure |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

onBundleBegin: (err: BusinessError, bundleName: string) => {
  if (err) {
    console.error(`onBundleBegin failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('onBundleBegin success');
}
```

## onBundleEnd

```TypeScript
onBundleEnd: AsyncCallback<string, void | string>
```

Callback called when a backup/restore procedure for an bundle ends successfully or gets aborted unexpectedly. The first return string parameter indicates the name of the bundle. The second return string parameter indicates that when BusinessError errors occur, the callback data is the name of the bundle.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string, void &#124; string&gt;

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 13500003 | Backup or restore timed out |
| 13500004 | Application extension death |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

onBundleEnd: (err: BusinessError, bundleName: string) => {
  if (err) {
    console.error(`onBundleEnd failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('onBundleEnd success');
}
```

## onFileReady

```TypeScript
onFileReady: AsyncCallback<File>
```

Callback called when the backup service tries to send files to the client. The File argument indicates a file to send to the client. The returned file is owned by the backup service and will be cleaned by the service once the file is closed.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[File](arkts-corefile-file-fs-file-i.md)&gt;

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

onFileReady: (err: BusinessError, file: backup.File) => {
  if (err) {
    console.error(`onFileReady failed. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`onFileReady success with file: ${file.bundleName}, ${file.uri}`);
  fileIo.closeSync(file.fd);
}
```

## onMigrateResult

```TypeScript
onMigrateResult?: AsyncCallback<string, void | string>
```

Callback called when the migrate result is reported. The first return string parameter indicates the name of the bundle. The second return string parameter indicates that when BusinessError errors occur, the callback data is the name of the bundle.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string, void &#124; string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13600001 | IPC error |
| 13900001 | Operation not permitted |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
