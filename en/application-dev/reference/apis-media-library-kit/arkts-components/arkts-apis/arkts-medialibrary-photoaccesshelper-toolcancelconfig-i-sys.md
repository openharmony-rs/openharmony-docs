# ToolCancelConfig (System API)

Configuration for canceling an analysis tool.

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

Parameters for canceling the analysis tool, in JSON string format. The total length must not exceed 16KB.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## taskId

```TypeScript
taskId: string
```

Task ID to cancel. It is a valid ID returned by **invokeAnalysisTool**.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
