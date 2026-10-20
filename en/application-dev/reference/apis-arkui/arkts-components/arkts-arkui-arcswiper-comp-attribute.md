# ArcSwiper properties/events

```TypeScript
declare class ArcSwiperAttribute extends CommonMethod<ArcSwiperAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** ArcSwiperAttribute extends CommonMethod&lt;ArcSwiperAttribute&gt;

**Since:** 18

<!--Device-unnamed-declare class ArcSwiperAttribute extends CommonMethod<ArcSwiperAttribute>--><!--Device-unnamed-declare class ArcSwiperAttribute extends CommonMethod<ArcSwiperAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## customContentTransition

```TypeScript
customContentTransition(transition: Optional<SwiperContentAnimatedTransition>)
```

Customizes the **ArcSwiper** page transition animation. During the finger swipe and transition animation, a callback is triggered frame by frame for all pages within the viewport. You can set attributes such as opacity, scale, and offset in the callback.

During finger-following swipes and post-release transition animations, the [SwiperContentTransitionProxy](arkts-arkui-arcswiper-comp-swipercontenttransitionproxy-i.md) callback is invoked for all pages in the viewport on a frame-by-frame basis. For example, when there are two pages whose subscripts are 0 and 1 in the viewport, two callbacks whose indexes are 0 and 1 are invoked in each frame.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SwiperContentAnimatedTransition](arkts-arkui-arcswiper-comp-swipercontentanimatedtransition-i.md)&gt; | Yes | Information about the **ArcSwiper** custom swipe animation, including **timeout** and **transition**. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the sensitivity of the rotating crown. The page switching of the **ArcSwiper** component can be controlled by rotating the crown. Different sensitivity levels adjust the response speed of crown scrolling. The higher the sensitivity, the larger the page switching step per unit rotation angle.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Sensitivity of the digital crown rotation. Setting different sensitivity levels adjusts the response speed of crown rotation.<br>Default value: CrownSensitivity.MEDIUM |

## disableSwipe

```TypeScript
disableSwipe(disabled: Optional<boolean>)
```

Sets whether to disable the swipe-to-switch feature of the component.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to disable the swipe-to-switch feature of the component. The value **true** means to disable the feature, and **false** means the opposite. <br>Default value: **false** |

## disableTransitionAnimation

```TypeScript
disableTransitionAnimation(disabled: Optional<boolean>)
```

Sets whether to disable special animation effects.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to disable the transition animation.<br>**true**: yes; **false**: no.<br>If an invalid parameter is passed, it is processed as **false**. |

## duration

```TypeScript
duration(duration: Optional<number>)
```

Sets the duration of the animation for child component switching.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-duration(duration: Optional<number>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-duration(duration: Optional<number>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Animation duration for child component switching.<br>Default value: **400** <br>Unit: ms. If a negative number is passed, the default value is used. |

## effectMode

```TypeScript
effectMode(edgeEffect: Optional<EdgeEffect>)
```

Sets effect used at the edges of the component when the boundary of the scrollable content is reached. For supported edge effects, see [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md). The bounce effect does not take effect when page turning is controlled through the **showNext**, **showPrevious**, and **finishAnimation** APIs of [ArcSwiperController](arkts-arkui-arcswiper-comp-arcswipercontroller-c.md).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| edgeEffect | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md)&gt; | Yes | Effect used at the edges of the component when the boundary of the scrollable content is reached. The bounce effect does not take effect when page turning is controlled through the **ArcSwiperController** API.<br>Default value: **EdgeEffect.Spring** |

## index

```TypeScript
index(index: Optional<number>)
```

Sets the index of the child component currently displayed in the container. If the **index** value is **undefined**, less than 0, or greater than or equal to the number of child components, the default value **0** is used.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-index(index: Optional<number>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-index(index: Optional<number>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Index of the child component currently displayed in the container. <br>If **index** is set to **undefined**, the value **0** is used. |

## indicator

```TypeScript
indicator(style: Optional<ArcDotIndicator | boolean>)
```

Sets the style of the arc dot navigation indicator.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ArcDotIndicator](arkts-arkui-arcswiper-comp-arcdotindicator-c.md) &#124; boolean&gt; | Yes | Style of the arc dot navigation indicator. <br> - **ArcDotIndicator**: properties and behavior of the arc dot navigation indicator. <br> - **boolean**: whether to enable the arc dot navigation indicator. **true** to enable, **false** otherwise. <br> Default value: **true** <br> Default type: **ArcDotIndicator** |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: Optional<AnimationEndHandler>)
```

Triggered when the page transition animation ends.

Triggered when the **ArcSwiper** transition animation ends, including when the animation is interrupted by a gesture or when **finishAnimation** is called through [ArcSwiperController](arkts-arkui-arcswiper-comp-arcswipercontroller-c.md). The parameter is the index value after the animation ends. For multi-column **ArcSwiper**, the **index** is the index of the leftmost component.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[AnimationEndHandler](arkts-arkui-arcswiper-comp-animationendhandler-t.md)&gt; | Yes | Triggered when the page transition animation ends. |

## onAnimationStart

```TypeScript
onAnimationStart(handler: Optional<AnimationStartHandler>)
```

Triggered when the page transition animation starts.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[AnimationStartHandler](arkts-arkui-arcswiper-comp-animationstarthandler-t.md)&gt; | Yes | Triggered when the page transition animation starts. |

## onChange

```TypeScript
onChange(handler: Optional<IndexChangedHandler>)
```

Triggered when the index of the currently displayed child component changes. The return value is the index of the currently displayed child component.

When the **ArcSwiper** component is used together with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), the subpage UI update cannot be triggered in the **onChange** event.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[IndexChangedHandler](arkts-arkui-arcswiper-comp-indexchangedhandler-t.md)&gt; | Yes | Callback for the index of the currently displayed element. |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: Optional<GestureSwipeHandler>)
```

Triggered on a frame-by-frame basis when the page is turned by a swipe.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[GestureSwipeHandler](arkts-arkui-arcswiper-comp-gestureswipehandler-t.md)&gt; | Yes | Triggered on a frame-by-frame basis when the page is turned by a swipe. |

## vertical

```TypeScript
vertical(isVertical: Optional<boolean>)
```

Sets whether vertical swiping is used.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperAttribute-vertical(isVertical: Optional<boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-vertical(isVertical: Optional<boolean>): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isVertical | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether vertical swiping is used. <br>The value **true** means vertical swiping, and **false** means horizontal swiping. <br>Default value: **false** |
