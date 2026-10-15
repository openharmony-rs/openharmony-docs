# SwiperContentAnimatedTransition

```TypeScript
declare interface SwiperContentAnimatedTransition
```

Provides the information about the custom page transition animation.

**Since:** 12

<!--Device-unnamed-declare interface SwiperContentAnimatedTransition--><!--Device-unnamed-declare interface SwiperContentAnimatedTransition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Timeout for the custom transition animation of the **Swiper**. The timing starts from the first frame when the page executes the default animation (page sliding) and moves out of the viewport. If the developer still has not called the **finishTransition** API of [SwiperContentTransitionProxy](arkts-arkui-swiper-comp-swipercontenttransitionproxy-i.md) to notify the **Swiper** component that the custom animation of this page has ended after this time is reached, the component considers that the custom animation of this page has ended and immediately removes the page node from the render tree. Unit: ms

Default value: **0**

Value range: [0, +∞). If a value less than 0 is set, the default value is used.

**Type:** number

**Default:** 0 ms

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-SwiperContentAnimatedTransition-timeout?: number--><!--Device-SwiperContentAnimatedTransition-timeout?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<SwiperContentTransitionProxy>
```

Content of the custom page transition animation.

**Type:** Callback&lt;[SwiperContentTransitionProxy](arkts-arkui-swiper-comp-swipercontenttransitionproxy-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>--><!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
