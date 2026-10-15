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

Timeout for the **ArcSwiper** custom swipe animation. The timer starts from the first frame when the page performs the default animation (page swipe) and moves out of the viewport. If the developer has not called the [finishTransition](arkts-arkui-arcswiper-comp-swipercontenttransitionproxy-i.md#finishtransition) API of [SwiperContentTransitionProxy](arkts-arkui-arcswiper-comp-swipercontenttransitionproxy-i.md) to notify the **ArcSwiper** component that the custom animation of this page has ended after this time is reached, the component will forcibly end the custom animation of this page and immediately render the tree under this page node.

Unit: ms

Default value: **0**.

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

**Type:** Callback&lt;[SwiperContentTransitionProxy](arkts-arkui-arcswiper-comp-swipercontenttransitionproxy-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>--><!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
