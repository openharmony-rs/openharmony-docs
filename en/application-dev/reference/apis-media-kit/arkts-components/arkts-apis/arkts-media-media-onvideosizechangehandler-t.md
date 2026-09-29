# OnVideoSizeChangeHandler

```TypeScript
type OnVideoSizeChangeHandler = (width: number, height: number) => void
```

Describes the callback invoked for the video size change event.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-media-type OnVideoSizeChangeHandler = (width: int, height: int) => void--><!--Device-media-type OnVideoSizeChangeHandler = (width: int, height: int) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Video width, in px. |
| height | number | Yes | Video height, in px. |
