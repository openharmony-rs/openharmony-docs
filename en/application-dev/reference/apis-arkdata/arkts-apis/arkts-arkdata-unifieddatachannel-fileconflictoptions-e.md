# FileConflictOptions

```TypeScript
enum FileConflictOptions
```

Enumerates the options for resolving file copy conflicts.

**Since:** 15

<!--Device-unifiedDataChannel-enum FileConflictOptions--><!--Device-unifiedDataChannel-enum FileConflictOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

Overwrite the file with the same name in the destination directory.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-FileConflictOptions-OVERWRITE = 0--><!--Device-FileConflictOptions-OVERWRITE = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SKIP

```TypeScript
SKIP = 1
```

Skip the file if there is a file with the same name in the destination directory.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-FileConflictOptions-SKIP = 1--><!--Device-FileConflictOptions-SKIP = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
