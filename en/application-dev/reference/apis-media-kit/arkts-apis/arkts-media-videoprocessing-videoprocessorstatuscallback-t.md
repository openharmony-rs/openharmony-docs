# VideoProcessorStatusCallback

```TypeScript
type VideoProcessorStatusCallback = (status: VideoProcessorStatus) => void
```

Status change callback type for video processor notifications.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-videoProcessing-type VideoProcessorStatusCallback = (status: VideoProcessorStatus) => void--><!--Device-videoProcessing-type VideoProcessorStatusCallback = (status: VideoProcessorStatus) => void-End-->

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [VideoProcessorStatus](arkts-media-videoprocessing-videoprocessorstatus-i.md) | Yes | The type of video processor status. |
