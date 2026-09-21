# SwiperContentAnimatedTransition

```TypeScript
declare interface SwiperContentAnimatedTransition
```

Provides the information about the custom page transition animation.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Timeout for the page transition animation. The timeout timer starts when the default animation (page scrolling) reaches the point where the first frame is moved out of the viewport. If you do not call the **finishTransition** API of [SwiperContentTransitionProxy](arkts-arkui-swiper-comp-swipercontenttransitionproxy-i.md) before the timer expires, the component considers that the custom animation of the page ends and immediately removes the page node from the render tree. The unit is ms. The default value is **0**.

**Type:** number

**Default:** 0 ms

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
