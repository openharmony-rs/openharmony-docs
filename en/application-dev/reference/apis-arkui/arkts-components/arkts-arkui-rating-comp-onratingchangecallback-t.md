# OnRatingChangeCallback

```TypeScript
declare type OnRatingChangeCallback = (rating: number) => void
```

Called when the rating value changes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnRatingChangeCallback = (rating: number) => void--><!--Device-unnamed-declare type OnRatingChangeCallback = (rating: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rating | number | Yes | Rating value. The value range is [0, **stars**]. |
