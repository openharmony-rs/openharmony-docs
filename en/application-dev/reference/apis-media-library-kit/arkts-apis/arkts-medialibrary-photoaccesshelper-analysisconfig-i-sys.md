# AnalysisConfig (System API)

Defines the asset analysis configuration.

**Since:** 24

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraInfos

```TypeScript
extraInfos?: string
```

Extended information in JSON string format.

Length range: (0, 500].

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## types

```TypeScript
types: AnalysisType[]
```

Array of intelligent analysis types. The maximum size of the array is the number of members defined by the [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) enum.

**Type:** [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md)[]

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## uris

```TypeScript
uris: string[]
```

Asset URI array.

Length range: [0, 100].

**Type:** string[]

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
