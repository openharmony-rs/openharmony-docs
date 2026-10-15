# HydrateProgress (System API)

```TypeScript
interface HydrateProgress
```

Encapsulates the hydrate progress information.

**Since:** 26.0.1

<!--Device-cloudDiskManager-interface HydrateProgress--><!--Device-cloudDiskManager-interface HydrateProgress-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## filePath

```TypeScript
filePath: string
```

Original absolute path of the file, consistent with the one passed in to hydratePlaceholder. The maximum length is 4096 and cannot be empty.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgress-filePath: string--><!--Device-HydrateProgress-filePath: string-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## processedSize

```TypeScript
processedSize: number
```

Number of bytes downloaded. Valid only when state is IN_PROGRESS. Unit: Byte.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgress-processedSize: long--><!--Device-HydrateProgress-processedSize: long-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## state

```TypeScript
state: HydrateProgressState
```

State of the hydrate progress.

**Type:** [HydrateProgressState](arkts-corefile-clouddiskmanager-hydrateprogressstate-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgress-state: HydrateProgressState--><!--Device-HydrateProgress-state: HydrateProgressState-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## totalSize

```TypeScript
totalSize: number
```

Total size of the file being hydrated, in bytes. Unit: Byte.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HydrateProgress-totalSize: long--><!--Device-HydrateProgress-totalSize: long-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.
