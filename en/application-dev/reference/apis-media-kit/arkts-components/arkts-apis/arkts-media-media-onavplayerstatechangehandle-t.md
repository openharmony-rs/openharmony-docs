# OnAVPlayerStateChangeHandle

```TypeScript
type OnAVPlayerStateChangeHandle = (state: AVPlayerState, reason: StateChangeReason) => void
```

Describes the callback invoked for the AVPlayer state change event.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-media-type OnAVPlayerStateChangeHandle = (state: AVPlayerState, reason: StateChangeReason) => void--><!--Device-media-type OnAVPlayerStateChangeHandle = (state: AVPlayerState, reason: StateChangeReason) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [AVPlayerState](arkts-media-media-avplayerstate-t.md) | Yes | State of the AVPlayer. |
| reason | [StateChangeReason](arkts-media-media-statechangereason-e.md) | Yes | Reason for the state change. |
