# VideoProcessor

Provides the VideoProcessor type, including AIHDR related functions.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

## Modules to Import

```TypeScript
import { videoProcessing } from '@kit.MediaKit';
```

## getStatus

```TypeScript
getStatus(): Promise<VideoProcessorStatus | undefined>
```

Gets the current status of video processor features.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[VideoProcessorStatus](arkts-media-videoprocessing-videoprocessorstatus-i.md) &#124; undefined&gt; | Promise used to return VideoProcessorStatus or undefined. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

## offStatusChange

```TypeScript
offStatusChange(callback?: VideoProcessorStatusCallback): void
```

Unregisters a listener for video processor status changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [VideoProcessorStatusCallback](arkts-media-videoprocessing-videoprocessorstatuscallback-t.md) | No | The callback function to remove. If not provided, all callbacks for this event type will be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [29200006](../../apis-image-kit/errorcode-videoprocessingengine.md#29200006-operation-not-allowed) | The operation is not permitted. This may be caused by incorrect status. |
| [29200009](../../apis-image-kit/errorcode-videoprocessingengine.md#29200009-invalid-value) | Input value is invalid. |

## onStatusChange

```TypeScript
onStatusChange(callback: VideoProcessorStatusCallback): void
```

Registers a listener for video processor status changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [VideoProcessorStatusCallback](arkts-media-videoprocessing-videoprocessorstatuscallback-t.md) | Yes | The callback function to invoke when status changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [29200007](../../apis-image-kit/errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |
| [29200009](../../apis-image-kit/errorcode-videoprocessingengine.md#29200009-invalid-value) | Input value is invalid. |
