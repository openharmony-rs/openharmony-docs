# OnPlaybackRateDone

```TypeScript
type OnPlaybackRateDone = (rate: number) => void
```

Describes the callback invoked for the event indicating that the playback rate setting is complete.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-media-type OnPlaybackRateDone = (rate: double) => void--><!--Device-media-type OnPlaybackRateDone = (rate: double) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rate | number | Yes | Playback rate. |
