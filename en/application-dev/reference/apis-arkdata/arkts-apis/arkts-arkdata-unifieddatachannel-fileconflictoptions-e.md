# FileConflictOptions

```TypeScript
enum FileConflictOptions
```

Enumerates the optional policies for file copy conflicts.

**Since:** 15

<!--Device-unifiedDataChannel-enum FileConflictOptions--><!--Device-unifiedDataChannel-enum FileConflictOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

Overwrites the file when a file with the same name exists in the destination path.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-FileConflictOptions-OVERWRITE = 0--><!--Device-FileConflictOptions-OVERWRITE = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SKIP

```TypeScript
SKIP = 1
```

Skips the file when a file with the same name exists in the destination path.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-FileConflictOptions-SKIP = 1--><!--Device-FileConflictOptions-SKIP = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
