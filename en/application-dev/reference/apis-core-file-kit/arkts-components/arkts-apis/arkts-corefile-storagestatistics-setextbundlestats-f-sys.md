# setExtBundleStats (System API)

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## setExtBundleStats

```TypeScript
function setExtBundleStats(userId: number, stats: ExtBundleStats): Promise<void>
```

Reports the space usage of system applications or system services. This API uses a promise to return the result.

> **NOTE:** 
> 
> If the value of **flag** in **stats** is **false**, the value of **businessName** must be the bundle name of an
> application.

**Since:** 23

**Required permissions:** ohos.permission.STORAGE_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| stats | [ExtBundleStats](arkts-corefile-storagestatistics-extbundlestats-i-sys.md) | Yes | Space usage of system applications or system services. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600010 | The input parameter is invalid. |
| 13600011 | Failed to report the specified business space usage. |

**Examples**

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extBundleStats: storageStatistics.ExtBundleStats = {
  businessName: 'com.example.storagedemo',
  size: 10000,
  flag: true
}
storageStatistics.setExtBundleStats(userId, extBundleStats).then(() => {
  console.info("setExtBundleStats successfully");
}).catch((err: BusinessError) => {
  console.error(`setExtBundleStats failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```
