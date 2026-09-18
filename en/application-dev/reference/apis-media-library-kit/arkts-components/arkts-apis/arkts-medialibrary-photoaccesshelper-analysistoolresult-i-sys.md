# AnalysisToolResult (System API)

Result of an analysis tool execution.

**Since:** 26.1.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## errCode

```TypeScript
errCode: number
```

Error code of the tool execution. The value 0 indicates success. Possible error codes: <br>23800203 - Temperature is too high. <br>23800204 - Battery level is too low. <br>23800205 - Storage space is insufficient. <br>23800206 - Power saving mode is enabled. <br>23800207 - Intelligent analysis service is already running. <br>23800208 - Intelligent analysis switch is disabled. <br>23800209 - Analysis service error. Check the logs for details. <br>23800301 - Internal system error.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## result

```TypeScript
result?: string
```

Result of the tool execution, in JSON string format.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
