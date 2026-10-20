# getTotalSizeSync

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getTotalSizeSync

```TypeScript
function getTotalSizeSync(): number
```

Obtains the total space of the built-in storage, in bytes. This API returns the result synchronously.

**Since:** 15

<!--Device-storageStatistics-function getTotalSizeSync(): long--><!--Device-storageStatistics-function getTotalSizeSync(): long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value:**

| Type | Description |
| --- | --- |
| number | Built-in storage space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let number = storageStatistics.getTotalSizeSync();
  console.info("getTotalSizeSync successfully:" + JSON.stringify(number));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getTotalSizeSync failed with error:" + JSON.stringify(error));
}
```
