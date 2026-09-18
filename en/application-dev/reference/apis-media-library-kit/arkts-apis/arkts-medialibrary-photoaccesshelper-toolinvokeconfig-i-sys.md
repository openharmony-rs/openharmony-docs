# ToolInvokeConfig (System API)

Configuration for invoking an analysis tool.

**Since:** 26.1.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## param

```TypeScript
param?: string
```

Parameters of the analysis tool to invoke, in JSON string format. The total length must not exceed 16KB.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## type

```TypeScript
type: AnalysisToolType
```

Type of the analysis tool to invoke.

**Type:** [AnalysisToolType](arkts-medialibrary-photoaccesshelper-analysistooltype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
