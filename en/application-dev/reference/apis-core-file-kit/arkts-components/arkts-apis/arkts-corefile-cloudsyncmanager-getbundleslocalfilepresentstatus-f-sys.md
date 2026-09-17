# getBundlesLocalFilePresentStatus (System API)

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## getBundlesLocalFilePresentStatus

```TypeScript
function getBundlesLocalFilePresentStatus(bundleNames: Array<string>): Promise<Array<LocalFilePresentStatus>>
```

Obtains the existence status of local files for multiple applications and checks whether there are files that have not been uploaded to the cloud in the cloud storage space. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleNames | Array&lt;string&gt; | Yes | Array of application bundle names to be checked. Each element is the bundle name of an application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[LocalFilePresentStatus](arkts-corefile-cloudsyncmanager-localfilepresentstatus-i-sys.md)&gt;&gt; | Promise used to return an array of objects. Each object in the array contains the bundle name of the application to be checked and the local file existence status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameter are left unspecified. 2.The length of the input parameter exceeds the upper limit. <br>3.The input parameter contains an invalid bundleName. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getBundlesLocalFilePresentStatus(bundles).then((results: Array<cloudSyncManager.LocalFilePresentStatus>) => {
  results.forEach((item) => {
    console.info(`bundle: ${item.bundleName}, hasLocalUncloudedFiles: ${item.isLocalFilePresent}`);
  });
}).catch((err: BusinessError) => {
  console.error(`getBundlesLocalFilePresentStatus failed, code: ${err.code}, message: ${err.message}`);
});
```
