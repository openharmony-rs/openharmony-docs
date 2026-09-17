# DeepOptimizeSpaceProgress (System API)

Defines the DeepOptimizeSpaceProgress data structure.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## progress

```TypeScript
progress: number
```

The percentage of deep optimize space state. Unit: Percentage, The value range is all integers, Value range: [0, 100].

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## state

```TypeScript
state: DeepOptimizeState
```

The current deep optimize space state.

**Type:** [DeepOptimizeState](arkts-medialibrary-photoaccesshelper-deepoptimizestate-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
