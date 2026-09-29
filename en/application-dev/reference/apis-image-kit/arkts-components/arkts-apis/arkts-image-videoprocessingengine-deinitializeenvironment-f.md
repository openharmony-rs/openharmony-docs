# deinitializeEnvironment

## Modules to Import

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';
```

## deinitializeEnvironment

```TypeScript
function deinitializeEnvironment(): Promise<void>
```

Deinitialize global environment for image processing.

**Since:** 18

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 18.

<!--Device-videoProcessingEngine-function deinitializeEnvironment(): Promise<void>--><!--Device-videoProcessingEngine-function deinitializeEnvironment(): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [29200006](../errorcode-videoprocessingengine.md#29200006-operation-not-allowed) | The operation is not permitted. This may be caused by incorrect status. |

**Examples**

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';

async function deinitializeEnvironment() {
  videoProcessingEngine.initializeEnvironment();
  videoProcessingEngine.deinitializeEnvironment();
}
```
