# AnalysisConfig (System API)

```TypeScript
interface AnalysisConfig
```

Defines the asset analysis configuration.

**Since:** 24

<!--Device-photoAccessHelper-interface AnalysisConfig--><!--Device-photoAccessHelper-interface AnalysisConfig-End-->

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

<!--Device-AnalysisConfig-extraInfos?: string--><!--Device-AnalysisConfig-extraInfos?: string-End-->

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

<!--Device-AnalysisConfig-types: AnalysisType[]--><!--Device-AnalysisConfig-types: AnalysisType[]-End-->

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

<!--Device-AnalysisConfig-uris: string[]--><!--Device-AnalysisConfig-uris: string[]-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
