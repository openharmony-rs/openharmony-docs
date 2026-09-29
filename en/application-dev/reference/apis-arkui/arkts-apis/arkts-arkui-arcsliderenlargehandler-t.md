# ArcSliderEnlargeHandler

```TypeScript
declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void
```

Triggered when the arc slider is enlarged or shrunk.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void--><!--Device-unnamed-declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnlarged | boolean | Yes | Whether the arc slider is enlarged.<br>**false**: The arc slider is in a reduced state. <br>**true**: The arc slider is in an enlarged state. |
