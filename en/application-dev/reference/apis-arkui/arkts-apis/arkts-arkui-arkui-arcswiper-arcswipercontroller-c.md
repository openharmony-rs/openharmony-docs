# ArcSwiperController

Implements the controller of the **ArcSwiper** component. You can bind this object to the **ArcSwiper** component and use it to control page switching.

**Since:** 18

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

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## finishAnimation

```TypeScript
finishAnimation(handler?: FinishAnimationHandler)
```

Stops an animation.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [FinishAnimationHandler](arkts-arkui-finishanimationhandler-t.md) | No | Callback invoked when the animation stops.<br>If no value is provided, no callback is performed. |

## showNext

```TypeScript
showNext()
```

Turns to the next page. Page turning occurs with the animation, whose duration is specified by [duration](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md#duration).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## showPrevious

```TypeScript
showPrevious()
```

Turns to the previous page. Page turning occurs with the animation, whose duration is specified by [duration](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md#duration).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
