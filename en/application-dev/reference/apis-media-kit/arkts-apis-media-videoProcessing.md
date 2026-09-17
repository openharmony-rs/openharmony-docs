# @ohos.multimedia.videoProcessing (Video Processing)

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhuyicheng666-->
<!--Designer: @gongzheng92-->
<!--Tester: @gongzheng92-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b59cf3021b187226962e426a7d120958dfd14aa4 translatedAt=2026-08-25T10:02:27.761Z pushedAt=2026-08-25T12:10:16.773Z -->

This module provides APIs for video quality processing. Currently, video AI-HDR enhancement is supported.

AI-HDR (Artificial Intelligence High Dynamic Range) is a technology that uses AI algorithms to enhance video quality. It can enhance the brightness, contrast, and color of videos, expand the video dynamic range, enrich details in the highlights and dark regions, and improve the visual effects and impact of videos.

With this module, you can create a [VideoProcessor](#videoprocessor) instance, query the current status of AI-HDR enhancement, and register a listener for status changes. In this way, you can detect and handle status changes of AI-HDR enhancement in a timely manner.

You can use the APIs of this module to check whether this function is enabled.

Before using the APIs of this module, you need to obtain a [VideoProcessor](#videoprocessor) instance by calling [videoProcessing.createVideoProcessor](#videoprocessingcreatevideoprocessor). When the app exits or the video processing capability is no longer needed, you can release related resources.

> **NOTE**
>
> This API can be used only in the stage model.

**Since**: 26.0.0

## Modules to Import

```ts
import { videoProcessing } from '@kit.MediaKit';
```

## videoProcessing.createVideoProcessor

createVideoProcessor(): VideoProcessor

Creates a **VideoProcessor** instance. If the operation is successful, a **VideoProcessor** instance is returned. Otherwise, **null** is returned.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Return value**

| Type | Description |
| ------------ | ------------ |
| [VideoProcessor](#videoprocessor) | Pointer to the **VideoProcessor** instance. If the operation is successful, a **VideoProcessor** instance is returned. Otherwise, **null** is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Video Processing Engine Error Codes](../apis-image-kit/errorcode-videoprocessingengine.md).

| ID | Error Information |
| :------------ | :------------ |
| 801 | Capability not supported. Function createVideoProcessor can not work correctly due to limited device capabilities. |
| 29200003 | Failed to create video processing instance. For example, the number of instances exceeds the upper limit. |
| 29200007 | Out of memory. |

**Example**

```ts
import { videoProcessing } from '@kit.MediaKit';

function createVideoProcessor() {
  let videoProcessor = videoProcessing.createVideoProcessor();
}
```

## VideoProcessor

Defines a video processing class, which provides APIs for video quality processing. Currently, AI-HDR enhancement is supported.

**Since**: 26.0.0

### getStatus

getStatus(): Promise\<VideoProcessorStatus | undefined\>

Obtains the status of the video processor features. This API uses a promise to return the result asynchronously.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Return value**

| Type | Description |
| ------------ | ------------ |
| Promise\<[VideoProcessorStatus](#videoprocessorstatus) \| undefined\> | Promise used to return the video processor status. If the operation fails, **undefined** is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information |
| :------------ | :------------ |
| 801 | Capability not supported. |

**Example**

```ts
import { videoProcessing } from '@kit.MediaKit';

async function getStatus() {
  let videoProcessor = videoProcessing.createVideoProcessor();
  let status = await videoProcessor.getStatus();
  if (status !== undefined && status.aiHdr !== undefined) {
    console.info('AIHDR enabled: ' + status.aiHdr.enabled);
  }
}
```

### onStatusChange

onStatusChange(callback: VideoProcessorStatusCallback): void

Registers a listener for video processor status changes. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters**

| Name | Type | Mandatory | Description |
| :------------ | :------------ | :------------ | :------------ |
| callback | [VideoProcessorStatusCallback](#videoprocessorstatuscallback) | Yes | Callback invoked when the status changes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Video Processing Engine Error Codes](../apis-image-kit/errorcode-videoprocessingengine.md).

| ID | Error Information |
| :------------ | :------------ |
| 801 | Capability not supported. |
| 29200007 | Out of memory. |
| 29200009 | Input value is invalid. |

**Example**

```ts
import { videoProcessing } from '@kit.MediaKit';

function onStatusChange() {
  let videoProcessor = videoProcessing.createVideoProcessor();
  videoProcessor.onStatusChange((status: videoProcessing.VideoProcessorStatus) => {
    if (status !== undefined && status.aiHdr !== undefined) {
      console.info('AIHDR status changed, enabled: ' + status.aiHdr.enabled);
    }
  });
}
```

### offStatusChange

offStatusChange(callback?: VideoProcessorStatusCallback): void

Unregisters the listener for video processor status changes.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters**

| Name | Type | Mandatory | Description |
| :------------ | :------------ | :------------ | :------------ |
| callback | [VideoProcessorStatusCallback](#videoprocessorstatuscallback) | No | Callback to be removed. If this parameter is not specified, all callbacks corresponding the event type will be removed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Video Processing Engine Error Codes](../apis-image-kit/errorcode-videoprocessingengine.md).

| ID | Error Information |
| :------------ | :------------ |
| 801 | Capability not supported. |
| 29200006 | The operation is not permitted. This may be caused by incorrect status. |
| 29200009 | Input value is invalid. |

**Example**

```ts
import { videoProcessing } from '@kit.MediaKit';

function offStatusChange() {
  let videoProcessor = videoProcessing.createVideoProcessor();
  videoProcessor.offStatusChange();
}
```

## VideoProcessorStatus

Describes the unified status of the video processor.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

| Name  | Type  | Read-only  | Optional  | Description  |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| aiHdr | [VideoProcessorAiHdrStatus](#videoprocessoraihdrstatus) | No  | Yes  | AI-HDR enhancement. |

## VideoProcessorAiHdrStatus

Describes the AI HDR enhancement status.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

| Name  | Type  | Read-Only  | Optional  | Description  |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| enabled | boolean | No  | Yes  | Whether the AI HDR enhancement feature is enabled.<br>The value **true** indicates that the AI HDR enhancement feature is enabled, and the value **false** indicates that it is disabled. |

## VideoProcessorStatusCallback

type VideoProcessorStatusCallback = (status: VideoProcessorStatus) => void

Describes the callback type for video processor status changes.

**Since**: 26.0.0

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters**

| Name   | Type   | Mandatory | Description                                                         |
| ------ | ------ | ------ | ---------------------------------------------------------- |
| status | [VideoProcessorStatus](#videoprocessorstatus) | Yes | Video processor status after the change. |