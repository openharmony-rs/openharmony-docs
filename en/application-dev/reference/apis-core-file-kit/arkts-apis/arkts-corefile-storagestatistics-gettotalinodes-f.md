# getTotalInodes

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getTotalInodes

```TypeScript
function getTotalInodes(): Promise<number>
```

Get the total inodes.

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
| 13600016 | Failed to query the inode information of the data partition. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getTotalInodes().then((totalInodes: number) => {
  console.info("getTotalInodes successfully: " + totalInodes);
}).catch((err: BusinessError) => {
  console.error(`getTotalInodes failed. Code: ${err.code}, Message: ${err.message}`);
});
```
