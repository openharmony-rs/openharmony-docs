# getDowngradeDownloadTaskState (System API)

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## getDowngradeDownloadTaskState

```TypeScript
function getDowngradeDownloadTaskState(bundleNames: Array<string>): Promise<Array<DownloadProgress>>
```

Supports querying the execution status of full data download tasks for integrated cloud drive applications.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CLOUDFILE_SYNC_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleNames | Array&lt;string&gt; | Yes | array of bundleName. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DownloadProgress](arkts-corefile-cloudsyncmanager-downloadprogress-c.md)&gt;&gt; | Return Promise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameter are left unspecified. <br>2.The length of the input parameter exceeds the upper limit. Maximum array length is 20. <br>3.The input parameter contains an invalid bundleName. |
