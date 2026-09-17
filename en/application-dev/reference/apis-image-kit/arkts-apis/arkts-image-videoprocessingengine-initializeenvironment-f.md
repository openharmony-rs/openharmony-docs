# initializeEnvironment

## Modules to Import

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';
```

## initializeEnvironment

```TypeScript
function initializeEnvironment(): Promise<void>
```

Initialize global environment for image processing.

**Since:** 18

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function initializeEnvironment can not work correctly<br>due to limited device capabilities. |
| [29200002](../errorcode-videoprocessingengine.md#29200002-initialization-failure) | The global environment initialization for image processing failed,<br>such as failure to initialize the GPU environment. |
| [29200006](../errorcode-videoprocessingengine.md#29200006-operation-not-allowed) | The operation is not permitted. This may be caused by incorrect status. |
| [29200007](../errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |

**Examples**

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';

async function initializeEnvironment() {
  videoProcessingEngine.initializeEnvironment();
}
```
