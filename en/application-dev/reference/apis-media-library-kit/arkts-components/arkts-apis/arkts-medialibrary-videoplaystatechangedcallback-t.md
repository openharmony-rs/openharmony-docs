# videoPlayStateChangedCallback

```TypeScript
export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void
```

Callback to be invoked when the video playback state on a photo browser page changes.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [VideoPlayerState](arkts-medialibrary-file-photopickercomponent-videoplayerstate-e.md) | Yes | Enumerates the video playback states. |
