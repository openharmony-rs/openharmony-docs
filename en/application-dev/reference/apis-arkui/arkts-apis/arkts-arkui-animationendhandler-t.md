# AnimationEndHandler

```TypeScript
declare type AnimationEndHandler = (index: number, event: SwiperAnimationEvent) => void
```

Defines the callback triggered when the page transition animation ends.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element. |
| event | [SwiperAnimationEvent](../arkts-components/arkts-arkui-swiperanimationevent-i.md) | Yes | Extra information of the animation, which is the offset of the currently displayed element relative to the start position of the **ArcSwiper** along the main axis. |
