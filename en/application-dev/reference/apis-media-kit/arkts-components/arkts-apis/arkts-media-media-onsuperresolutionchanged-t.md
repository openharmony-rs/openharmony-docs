# OnSuperResolutionChanged

```TypeScript
type OnSuperResolutionChanged = (enabled: boolean) => void
```

Describes the callback used to listen for video super resolution status changes. If super resolution is enabled by using [PlaybackStrategy](arkts-media-media-playbackstrategy-i.md), this callback is invoked to report the super resolution status changes. It is also invoked to report the initial status when the video starts. However, this callback is not invoked when super resolution is not enabled.

Super resolution is automatically disabled in either of the following cases:

* The current super resolution algorithm only works with videos that have a frame rate of 30 fps or lower. If the video frame rate exceeds 30 fps, or if the input frame rate exceeds the processing capability of the super resolution algorithm in scenarios such as fast playback, super resolution is automatically disabled.  
* The current super resolution algorithm supports input resolutions from 320 × 320 to 1920 × 1080, in px. If the input video resolution exceeds the range during playback, super resolution is automatically disabled.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether super resolution is enabled. **true** if enabled, **false** otherwise. |
