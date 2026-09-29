# SwiperContentAnimatedTransition

```TypeScript
declare interface SwiperContentAnimatedTransition
```

Provides the information about the custom page transition animation.

**Since:** 18

<!--Device-unnamed-declare interface SwiperContentAnimatedTransition--><!--Device-unnamed-declare interface SwiperContentAnimatedTransition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## timeout

```TypeScript
timeout?: number
```

Timeout for the custom page transition animation. The timeout timer starts when the default animation (page scrolling) reaches the point where the first frame is moved out of the viewport. If you do not call the [finishTransition](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md#finishtransition) API of [SwiperContentTransitionProxy](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md) before the timer expires, the component considers that the custom animation of the page ends and immediately removes the page node from the render tree. The unit is ms. The default value is **0**.

**Type:** number

**Default:** 0 ms

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SwiperContentAnimatedTransition-timeout?: number--><!--Device-SwiperContentAnimatedTransition-timeout?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## transition

```TypeScript
transition: Callback<SwiperContentTransitionProxy>
```

Content of the custom page transition animation.

**Type:** Callback&lt;[SwiperContentTransitionProxy](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>--><!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
