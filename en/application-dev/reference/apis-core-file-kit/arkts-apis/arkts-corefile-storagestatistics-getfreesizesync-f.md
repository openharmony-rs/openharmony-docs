# getFreeSizeSync

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getFreeSizeSync

```TypeScript
function getFreeSizeSync(): number
```

Obtains the available space of the built-in storage, in bytes. This API returns the result synchronously.

**Since:** 15

<!--Device-storageStatistics-function getFreeSizeSync(): long--><!--Device-storageStatistics-function getFreeSizeSync(): long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**Return value:**

| Type | Description |
| --- | --- |
| number | Available space of the built-in storage obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let number = storageStatistics.getFreeSizeSync();
  console.info("getFreeSizeSync successfully:" + JSON.stringify(number));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getFreeSizeSync failed with error:" + JSON.stringify(error));
}
```
