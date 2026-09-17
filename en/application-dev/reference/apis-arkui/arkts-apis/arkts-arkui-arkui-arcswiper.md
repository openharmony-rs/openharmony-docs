# @ohos.arkui.ArcSwiper

## Modules to Import

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | Describes the properties and behavior of the arc dot navigation indicator. |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | In addition to the universal attributes, the following attributes are supported. |
| [ArcSwiperController](arkts-arkui-arkui-arcswiper-arcswipercontroller-c.md) | Implements the controller of the **ArcSwiper** component. You can bind this object to the **ArcSwiper** component and use it to control page switching. |

### Interfaces

| Name | Description |
| --- | --- |
| [ArcSwiperInterface](arkts-arkui-arkui-arcswiper-arcswiperinterface-i.md) | Provide an interface for ArcSwiper. |
| [SwiperContentAnimatedTransition](arkts-arkui-arkui-arcswiper-swipercontentanimatedtransition-i.md) | Provides the information about the custom page transition animation. |
| [SwiperContentTransitionProxy](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md) | Implements the proxy object returned during the execution of the custom page transition animation of the **ArcSwiper** component. You can use this object to obtain the page information in the custom animation viewport. You can also call the **finishTransition** API of this object to notify the **ArcSwiper** component that the custom animation has finished playing. |

### Enums

| Name | Description |
| --- | --- |
| [ArcDirection](arkts-arkui-arkui-arcswiper-arcdirection-e.md) | Declare the direction of arc indicator. |

### Types

| Name | Description |
| --- | --- |
| [AnimationEndHandler](arkts-arkui-animationendhandler-t.md) | Defines the callback triggered when the page transition animation ends. |
| [AnimationStartHandler](arkts-arkui-animationstarthandler-t.md) | Defines the callback triggered when the page transition animation starts. |
| [FinishAnimationHandler](arkts-arkui-finishanimationhandler-t.md) | Defines the callback to notify the application when the animation stops playing. |
| [GestureSwipeHandler](arkts-arkui-gestureswipehandler-t.md) | Defines the callback triggered on a frame-by-frame basis during a swipe-based page turn. |
| [IndexChangedHandler](arkts-arkui-indexchangedhandler-t.md) | Defines the callback to notify the application when the index of the currently displayed element changes. |

### Properties

| Name | Description |
| --- | --- |
| [ArcSwiper](arkts-arkui-ohosarkuiarcswiper-p.md) | Defines the ArcSwiper Component that can provide the ability for sub components to swipe and display. |
| [ArcSwiperInstance](arkts-arkui-ohosarkuiarcswiper-p.md) | Defines ArcSwiper Component instance. |

## Examples

```TypeScript
### Example 1: Configuring the Basic Attributes of ArcSwiper

This example demonstrates the basic functionality of the component by configuring the basic attributes of ArcSwiper.


```

```TypeScript
### Example 2: Customizing a Page Transition Animation for ArcSwiper

In this example, the customContentTransition API is used to define a custom switching animation for the ArcSwiper component.
```
