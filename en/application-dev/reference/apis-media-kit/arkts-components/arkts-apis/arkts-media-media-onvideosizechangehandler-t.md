# OnVideoSizeChangeHandler

```TypeScript
type OnVideoSizeChangeHandler = (width: number, height: number) => void
```

Describes the callback invoked for the video size change event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Video width, in px. |
| height | number | Yes | Video height, in px. |
