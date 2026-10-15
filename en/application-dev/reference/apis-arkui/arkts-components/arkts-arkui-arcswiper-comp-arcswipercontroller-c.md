# ArcSwiperController

```TypeScript
export class ArcSwiperController
```

Implements the controller of the **ArcSwiper** component. You can bind this object to the **ArcSwiper** component and use it to control page switching.

**Since:** 18

<!--Device-unnamed-export class ArcSwiperController--><!--Device-unnamed-export class ArcSwiperController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create an **ArcSwiperController** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperController-constructor()--><!--Device-ArcSwiperController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## finishAnimation

```TypeScript
finishAnimation(handler?: FinishAnimationHandler)
```

Stops the animation. When page switching is controlled through this method, the bounce effect set by **effectMode** does not take effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler)--><!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [FinishAnimationHandler](arkts-arkui-arcswiper-comp-finishanimationhandler-t.md) | No | Callback triggered when an animation stops.<br>Default value: No callback when not passed. |

## showNext

```TypeScript
showNext()
```

Swipes to the next page. The swipe transition includes animation, with the duration specified by [duration](arkts-arkui-arcswiper-comp-attribute.md#duration). When page switching is controlled through this method, the bounce effect set by **effectMode** does not take effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperController-showNext()--><!--Device-ArcSwiperController-showNext()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## showPrevious

```TypeScript
showPrevious()
```

Swipes to the previous page. The swipe transition includes animation, with the duration specified by [duration](arkts-arkui-arcswiper-comp-attribute.md#duration). When page switching is controlled through this method, the bounce effect set by **effectMode** does not take effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperController-showPrevious()--><!--Device-ArcSwiperController-showPrevious()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
