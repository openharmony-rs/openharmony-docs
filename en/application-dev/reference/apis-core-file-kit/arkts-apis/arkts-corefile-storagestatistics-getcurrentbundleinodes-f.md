# getCurrentBundleInodes

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getCurrentBundleInodes

```TypeScript
function getCurrentBundleInodes(): Promise<number>
```

Get the current bundle inodes.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | return Promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. |
| 13600002 | File system not supported. |
| 13600017 | Failed to query the inode information of the application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleInodes().then((curInodes: number) => {
  console.info("getCurrentBundleInodes successfully: " + curInodes);
}).catch((err: BusinessError) => {
  console.error(`getCurrentBundleInodes failed. Code: ${err.code}, Message: ${err.message}`);
});
```
