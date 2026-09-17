# createVideoProcessor

## Modules to Import

```TypeScript
import { videoProcessing } from '@kit.MediaKit';
```

## createVideoProcessor

```TypeScript
function createVideoProcessor(): VideoProcessor
```

Create a video processing instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Return value:**

| Type | Description |
| --- | --- |
| [VideoProcessor](arkts-media-videoprocessing-videoprocessor-i.md) | Returns the VideoProcessor instance if the operation is successful; returns null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function createVideoProcessor can not work correctly due to limited device capabilities. |
| [29200003](../../apis-image-kit/errorcode-videoprocessingengine.md#29200003-creation-failure) | Failed to create video processing instance. For example, the number of instances exceeds the upper limit. |
| [29200007](../../apis-image-kit/errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |
