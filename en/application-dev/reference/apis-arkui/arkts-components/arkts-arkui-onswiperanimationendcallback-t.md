# OnSwiperAnimationEndCallback

```TypeScript
declare type OnSwiperAnimationEndCallback = (index: number, extraInfo: SwiperAnimationEvent) => void
```

Defines the callback triggered when the page transition animation ends.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element. If there are multiple columns, **index** indicates the index of the leftmost component. |
| extraInfo | [SwiperAnimationEvent](arkts-arkui-swiperanimationevent-i.md) | Yes | Extra information of the animation, which is the offset of the currently displayed element relative to the start position of the **Swiper** along the main axis. |
