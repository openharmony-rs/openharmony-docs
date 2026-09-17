# listUserdataDirInfo (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## listUserdataDirInfo

```TypeScript
function listUserdataDirInfo(): Promise<Array<UserdataDirInfo>>
```

Queries the space usage of the **\/data** directory on the user device. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.STORAGE_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[UserdataDirInfo](arkts-corefile-storagestatistics-userdatadirinfo-i-sys.md)&gt;&gt; | Promise used to return the space usage of the **\/data** directory on the user device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600015 | Failed to traverse the query data partition directory. |

**Examples**

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.listUserdataDirInfo().then((dirInfos: storageStatistics.UserdataDirInfo[]) => {
  console.info("listUserdataDirInfo successfully.");
}).catch((err: BusinessError) => {
  console.error(`listUserdataDirInfo failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```
