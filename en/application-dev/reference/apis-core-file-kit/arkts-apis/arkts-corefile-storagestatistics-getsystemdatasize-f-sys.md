# getSystemDataSize (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getSystemDataSize

```TypeScript
function getSystemDataSize(): Promise<number>
```

Get the system data size.

**Since:** 24

**Required permissions:** ohos.permission.STORAGE_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | return Promise (Unit: Byte) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600018 | Failed to query the system data size. |

**Examples**

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemDataSize().then((systemDataSize: number) => {
  console.info("getSystemDataSize successfully: " + JSON.stringify(systemDataSize));
}).catch((err: BusinessError) => {
  console.error(`getSystemDataSize failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```
