# getExtBundleStats (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getExtBundleStats

```TypeScript
function getExtBundleStats(userId: number, businessName: string): Promise<ExtBundleStats>
```

Obtains the space usage of a specified user, system application bundle name, or system service name. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.STORAGE_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| businessName | string | Yes | System application bundle name or system service name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExtBundleStats](arkts-corefile-storagestatistics-extbundlestats-i-sys.md)&gt; | Promise used to return the space usage of a specified user, system application bundle name, or system service name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600010 | The input parameter is invalid. |
| 13600012 | Failed to query the specified business space usage. |

**Examples**

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let businessName: string = 'com.example.storagedemo';
storageStatistics.getExtBundleStats(userId, businessName).then((bundleStats: storageStatistics.ExtBundleStats) => {
  console.info("getExtBundleStats successfully.");
}).catch((err: BusinessError) => {
  console.error(`getExtBundleStats failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```
