# SwiperContentTransitionProxy

Implements the proxy object returned during the execution of the custom page transition animation of the **ArcSwiper** component. You can use this object to obtain the page information in the custom animation viewport. You can also call the **finishTransition** API of this object to notify the **ArcSwiper** component that the custom animation has finished playing.

> **NOTE:** 

> - For example, when the index of the currently selected child component is 0, during a transition animation from page 0 to page 1, the callback is triggered for all pages within the viewport on every frame. When pages 0 and 1are both in the viewport, the callback is triggered twice per frame. The first callback has **selectedIndex** as
> **0**, **index** as **0**, **position** as the ratio of how much page 0 has moved relative to its position before
> the animation started on the current frame, and **mainAxisLength** as the length of page 0 on the main axis. The
> second callback has **selectedIndex** as **0**, **index** as **1**, **position** as the ratio of how much page 1
> has moved relative to page 0 before the animation started on the current frame, and **mainAxisLength** as the
> length of page 1 on the main axis.
> 
> - If the animation curve is a spring interpolation curve, during the transition animation from page 0 to page 1,due to the position and velocity when the user lifts their finger off the screen, animation may overshoot and slide past to page 2, then bounce back to page 1. Throughout this process, a callback is triggered for pages 1 and 2within the viewport on every frame.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## finishTransition

```TypeScript
finishTransition(): void
```

Notifies the **ArcSwiper** component that the custom animation has finished playing.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## index

```TypeScript
index: number
```

Index of a page in the viewport.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## mainAxisLength

```TypeScript
mainAxisLength: number
```

Length of the page specified by **index** along the main axis. Unit: vp.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
position: number
```

Position of the page specified by **index** relative to the start position of the **ArcSwiper** main axis (start position of the page corresponding to **selectedIndex**).

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## selectedIndex

```TypeScript
selectedIndex: number
```

Index of the currently selected page.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
