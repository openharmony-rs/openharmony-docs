# AnimationStartHandler

```TypeScript
declare type AnimationStartHandler = (index: number, targetIndex: number, event: SwiperAnimationEvent) => void
```

Defines the callback triggered when the page transition animation starts.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element before the animation starts (not the final index after the animation ends). |
| targetIndex | number | Yes | Index of the target element to switch to. |
| event | [SwiperAnimationEvent](../arkts-components/arkts-arkui-swiperanimationevent-i.md) | Yes | Extra information of the animation, including the offset of the currently displayed element and target element relative to the start position of the **ArcSwiper** along the main axis, and the hands-off velocity. |
