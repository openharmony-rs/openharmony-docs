# disableCloud (System API)

## Modules to Import

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## disableCloud

```TypeScript
function disableCloud(accountId: string): Promise<void>
```

Disables device-cloud sync. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | Account ID. |

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

let accountId: string = "testAccount";
cloudSyncManager.disableCloud(accountId).then(() => {
  console.info("disableCloud successfully");
}).catch((err: BusinessError) => {
  console.error("disableCloud failed with error message: " + err.message + ", error code: " + err.code);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
cloudSyncManager.disableCloud(accountId, (err: BusinessError) => {
  if (err) {
    console.error("disableCloud failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("disableCloud successfully");
  }
});
```


## disableCloud

```TypeScript
function disableCloud(accountId: string, callback: AsyncCallback<void>): void
```

Disables device-cloud sync. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | string | Yes | Account ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result of disabling device-cloud sync. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**Examples**

See [disableCloud](#disablecloud)
