# ScrollableCommonMethod

```TypeScript
declare class ScrollableCommonMethod<T> extends CommonMethod<T>
```

CommonScrollableMethod

@extends CommonMethod&lt;T&gt;

**Inheritance/Implementation:** ScrollableCommonMethod extends CommonMethod<T>

**Since:** 12

<!--Device-unnamed-declare class ScrollableCommonMethod<T> extends CommonMethod<T>--><!--Device-unnamed-declare class ScrollableCommonMethod<T> extends CommonMethod<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoAdjustScrollBarMargin

```TypeScript
autoAdjustScrollBarMargin(enable: boolean | undefined): T
```

Sets whether to automatically adjust the margin of the scrollbar. By default, the margin is not automatically adjusted.

When the automatic margin adjustment feature is enabled, the scrolling direction of the scrollbar avoids the [padding](arkts-arkui-common-comp-commonmethod-c.md#padding), [safeAreaPadding](arkts-arkui-common-comp-commonmethod-c.md#safeareapadding) and [contentStartOffset](#contentstartoffset) /[contentEndOffset](#contentendoffset) areas of the component. If the [scrollBarMargin](#scrollbarmargin) attribute is set, this feature does not take effect. If the sum of the horizontal [padding](arkts-arkui-common-comp-commonmethod-c.md#padding), [safeAreaPadding](arkts-arkui-common-comp-commonmethod-c.md#safeareapadding), [contentStartOffset](#contentstartoffset) and [contentEndOffset](#contentendoffset) values is greater than the width of the component, or the sum of the vertical values is greater than the height of the component, the scrollbar is not displayed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollableCommonMethod-autoAdjustScrollBarMargin(enable: boolean | undefined): T--><!--Device-ScrollableCommonMethod-autoAdjustScrollBarMargin(enable: boolean | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to automatically adjust the margin.<br>**true**: yes. <br>**false**: no. <br>**undefined**: no. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## backToTop

```TypeScript
backToTop(backToTop: boolean): T
```

Sets whether to enable the back-to-top feature for the scrollable component when the status bar is touched.

When a status bar touch event is received, the scrollable component on the current page can scroll to the top with an animation. This behavior does not affect scrollable components in background applications, which will not scroll to the top. This attribute is independent of the [enableScrollInteraction](#enablescrollinteraction) setting.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ScrollableCommonMethod-backToTop(backToTop: boolean): T--><!--Device-ScrollableCommonMethod-backToTop(backToTop: boolean): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backToTop | boolean | Yes | Whether to enable the back-to-top feature for the scrollable component when the status bar is touched. **true** to enable, **false** otherwise.<br>Default value: <br>Versions earlier than API version 18: **false** <br>API version 18 and later: **false** for horizontal scrolling and **true** for vertical scrolling |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## clipContent

```TypeScript
clipContent(clip: ContentClipMode | RectShape): T
```

Sets the content clipping area for this scrollable component.

Since API version 26.0.0, child components within the content-layer clipping area can be displayed normally. In versions earlier than API version 26.0.0, when the content-layer clipping area of the [List](arkts-arkui-list-comp.md) component is larger than the component itself, child components that are completely outside the component area but within the clipping area are not displayed by default. To display them, set the **show** parameter of the **cachedCount** attribute of the component to **true**. However, because the preloaded child components set by the **cachedCount** attribute are executed only in idle time slots, flickering may occur due to untimely updates in scenarios such as component size changes and data updates.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ScrollableCommonMethod-clipContent(clip: ContentClipMode | RectShape): T--><!--Device-ScrollableCommonMethod-clipContent(clip: ContentClipMode | RectShape): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clip | [ContentClipMode](arkts-arkui-common-comp-contentclipmode-e.md) &#124; [RectShape](arkts-arkui-common-comp-rectshape-t.md) | Yes | Clipping applies only to the content of the scroll container, that is, its child nodes, and the background is not affected. When a custom rectangular area is passed in through **RectShape**, only the width, height, and [offset](../arkts-apis/arkts-arkui-arkui-shape-commonshapemethod-c.md#offset) relative to the upper left corner of the component are supported, and rounded corners are not supported. <br>Default value: the default value for **Grid** and **Scroll** is **ContentClipMode.BOUNDARY**, and the default value for **List** and **WaterFlow** is **ContentClipMode.CONTENT_ONLY**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## contentEndOffset

```TypeScript
contentEndOffset(offset: number | Resource): T
```

Sets the offset from the end of the content area. When the component scrolls to the end position, the content area maintains a specified distance from the component's display boundary.

If the combined value of contentStartOffset and contentEndOffset exceeds the scrollable content area length, both offsets are reset to 0.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ScrollableCommonMethod-contentEndOffset(offset: number | Resource): T--><!--Device-ScrollableCommonMethod-contentEndOffset(offset: number | Resource): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset of the end of the content area.<br>Default value: **0**<br>Unit: vp <br>Value range: [0, +∞)<br>If an invalid value such as a negative number or a non-numeric Resource is set, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## contentStartOffset

```TypeScript
contentStartOffset(offset: number | Resource): T
```

Sets the offset from the start of the content area. When the component scrolls to the start position, the content area maintains a specified distance from the component's display boundary.

If the combined value of contentStartOffset and contentEndOffset exceeds the scrollable content area length, both offsets are reset to 0.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ScrollableCommonMethod-contentStartOffset(offset: number | Resource): T--><!--Device-ScrollableCommonMethod-contentStartOffset(offset: number | Resource): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset of the start position of the content area.<br><br>the default value is used. <br>Unit: vp<br><br>If an invalid value such as a negative number or a non-numeric Resource is set. The value must be greater than or equal to 0. Default value: **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T
```

Sets the sensitivity of the digital crown's response to events.

A component must have focus to receive [crown events](arkts-arkui-common-comp.md). Focus control can be managed using [focusable](arkts-arkui-common-comp-commonmethod-c.md#focusable), [defaultFocus](arkts-arkui-common-comp-commonmethod-c.md#defaultfocus), and [focusOnTouch](arkts-arkui-common-comp-commonmethod-c.md#focusontouch).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ScrollableCommonMethod-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T--><!--Device-ScrollableCommonMethod-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Crown response sensitivity. **CrownSensitivity.LOW** indicates low sensitivity, with a slower scrolling response; **CrownSensitivity.MEDIUM** indicates medium sensitivity, with a moderate scrolling response; **CrownSensitivity.HIGH** indicates high sensitivity, with a faster scrolling response.<br>Default value: **CrownSensitivity.MEDIUM**, with a moderate response speed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T
```

Sets the effect used when the scroll boundary is reached.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T--><!--Device-ScrollableCommonMethod-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| edgeEffect | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.None** for the **Grid**, **Scroll**, and **WaterFlow** components and **EdgeEffect.Spring** for the **List** component |
| options | [EdgeEffectOptions](arkts-arkui-common-comp-edgeeffectoptions-i.md) | No | Whether to enable the sliding effect when the component content size is smaller than the component itself. Since API version 18, the edge where the edge effect takes effect can be set. Setting it to **{ alwaysEnabled: true }** enables the sliding effect, and **{ alwaysEnabled: false }** disables it.<br>Default value:<br>For the **List**, **Grid**, and **WaterFlow** components, the default value is **{ alwaysEnabled: false }**; for the **Scroll** component, the default value is **{ alwaysEnabled: true }**. Since API version 18, the **effectEdge** field is added by default, with the value **EffectEdge.START &#124; EffectEdge.END**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean): T
```

Sets whether to support scroll gestures.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-enableScrollInteraction(value: boolean): T--><!--Device-ScrollableCommonMethod-enableScrollInteraction(value: boolean): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support finger or mouse wheel gestures. The value **true** means supported, and **false** means not supported. However, this does not affect the scrolling APIs of the controller [Scroller](arkts-arkui-scroll-comp-scroller-c.md) or the [backToTop](#backtotop) attribute.<br>Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## enableScrollWithMouse

```TypeScript
enableScrollWithMouse(enabled: boolean | undefined): T
```

Sets whether to support scrolling by dragging with the left mouse button pressed. If this API is not called, scrolling by dragging with the left mouse button pressed is not supported by default.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollableCommonMethod-enableScrollWithMouse(enabled: boolean | undefined): T--><!--Device-ScrollableCommonMethod-enableScrollWithMouse(enabled: boolean | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Whether to support scrolling by dragging with the left mouse button pressed.<br>**true**: yes. <br>**false**: no. <br>**undefined**: no. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## fadingEdge

```TypeScript
fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T
```

Sets whether to enable the edge fading effect and the length of the fading edge.

> **NOTE:** 
> 
> **fadingEdge** is implemented by setting the [overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay) attribute and the
> [blendMode](arkts-arkui-common-comp-commonmethod-c.md#blendmode) attribute (with the parameter
> values **BlendMode.SRC_OVER** and **BlendApplyType.OFFSCREEN**). When **fadingEdge** takes effect, it overrides
> the **.overlay()** and **.blendMode()** attributes of the original component, and causes the APIs that require
> screen capture of the current component and its child components to fail to capture the correct image. The APIs
> that require screen capture include [blur](arkts-arkui-common-comp-commonmethod-c.md#blur),
> [linearGradientBlur](arkts-arkui-common-comp-commonmethod-c.md#lineargradientblur),
> [brightness](arkts-arkui-common-comp-commonmethod-c.md#brightness), [visualEffect](arkts-arkui-common-comp-commonmethod-c.md#visualeffect),
> [grayscale](arkts-arkui-common-comp-commonmethod-c.md#grayscale), [saturate](arkts-arkui-common-comp-commonmethod-c.md#saturate),
> [contrast](arkts-arkui-common-comp-commonmethod-c.md#contrast),
> [invert](arkts-arkui-common-comp-commonmethod-c.md#invert),
> [sepia](arkts-arkui-common-comp-commonmethod-c.md#sepia),
> [hueRotate](arkts-arkui-common-comp-commonmethod-c.md#huerotate),
> [colorBlend](arkts-arkui-common-comp-commonmethod-c.md#colorblend),
> [lightUpEffect](arkts-arkui-common-comp-commonmethod-c.md#lightupeffect),
> [pixelStretchEffect](arkts-arkui-common-comp-commonmethod-c.md#pixelstretcheffect),
> [blendMode](arkts-arkui-common-comp-commonmethod-c.md#blendmode), and
> [backgroundBrightness](arkts-arkui-common-comp-commonmethod-c.md#backgroundbrightness).
> 
> When **fadingEdge** takes effect, it is recommended not to set the [background](arkts-arkui-common-comp-commonmethod-c.md#background)
> related attributes on the component on which the **fadingEdge** attribute is set, because doing so affects the
> fading display effect.
> 
> When **fadingEdge** takes effect, it is recommended not to set the
> [systemMaterial](arkts-arkui-common-comp-commonmethod-c.md#systemmaterial) related attributes on the component on which the
> **fadingEdge** attribute is set or on its child components, because doing so affects the display effect of the
> system material and causes the material effect to be inconsistent with the expected effect.
> 
> When **fadingEdge** takes effect, the component on which the **fadingEdge** attribute is set is clipped to the
> boundary. Setting the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) attribute to **false** on this component
> does not take effect.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ScrollableCommonMethod-fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T--><!--Device-ScrollableCommonMethod-fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the edge fading effect. **true** to enable, **false** otherwise.<br>Default value: **false**. |
| options | [FadingEdgeOptions](arkts-arkui-common-comp-fadingedgeoptions-i.md) | No | Object defining edge fading effect properties, such as the fading edge length.<br>If the value is less than 0, undefined, or not set, the default value is used. The default length is 32 vp. <br>If the value exceeds half the height of the container, it is adjusted to exactly half the height of the container. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## flingSpeedLimit

```TypeScript
flingSpeedLimit(speedLimit: number): T
```

Sets the maximum initial speed for inertial animation after a fling gesture.

> **NOTE:** 
> 
> - Inertial animation is the effect that the scrolling content continues to scroll and gradually decelerates and stops after the finger quickly flings and leaves the screen. It is also called inertial scrolling.
> 
> - Inertial animation is triggered when the finger quickly flings and leaves the screen, or when the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) method is called.
> 
> - Inertial animation is not generated when the mouse wheel or keyboard arrow keys are used to scroll, or when the [scrollTo](arkts-arkui-scroll-comp-scroller-c.md#scrollto) method is used to scroll to a specified position.
> 
> - If the inertial animation is triggered by the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) method, the **flingSpeedLimit**setting does not take effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-flingSpeedLimit(speedLimit: number): T--><!--Device-ScrollableCommonMethod-flingSpeedLimit(speedLimit: number): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speedLimit | number | Yes | Maximum initial speed for inertial animation.<br>Default value: **9000** <br>Unit: vp/s <br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## friction

```TypeScript
friction(value: number | Resource): T
```

Sets the friction coefficient. It takes effect when the scroll area is swiped manually, and affects only the inertial scrolling process. It indirectly affects the linkage effect between nested scrollable components during inertial scrolling (for example, the chain animation [chainAnimation](arkts-arkui-list-comp-attribute.md#chainanimation) of the List component). It applies to scenarios where the deceleration speed of inertial scrolling needs to be adjusted. If the value is set to less than or equal to 0, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-friction(value: number | Resource): T--><!--Device-ScrollableCommonMethod-friction(value: number | Resource): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.6** for non-wearable devices and **0.9** for wearable devices. <br>Since API version 11, the default value for non-wearable devices is **0.7**. <br>Since API version 12, the default value for non-wearable devices is **0.75**. <br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions): T
```

Sets the nested scrolling mode in the forward and backward directions to implement scrolling linkage with the parent component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-nestedScroll(value: NestedScrollOptions): T--><!--Device-ScrollableCommonMethod-nestedScroll(value: NestedScrollOptions): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | Nested scrolling options.<br>Default value: **{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }** |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onDidScroll

```TypeScript
onDidScroll(handler: OnScrollCallback): T
```

Triggered when the scrollable component scrolls. The return value is the offset amount by which the list has scrolled and the current scroll state.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 14.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ScrollableCommonMethod-onDidScroll(handler: OnScrollCallback): T--><!--Device-ScrollableCommonMethod-onDidScroll(handler: OnScrollCallback): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md) | Yes | Callback triggered when the scrollable component scrolls. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onDidStopDragging

```TypeScript
onDidStopDragging(handler: OnDidStopDraggingCallback): T
```

Called when the scrollable component stops being dragged.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-ScrollableCommonMethod-onDidStopDragging(handler: OnDidStopDraggingCallback): T--><!--Device-ScrollableCommonMethod-onDidStopDragging(handler: OnDidStopDraggingCallback): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnDidStopDraggingCallback](arkts-arkui-common-comp-ondidstopdraggingcallback-t.md) | Yes | Callback invoked when the scrollable component stops being dragged. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onDidStopFling

```TypeScript
onDidStopFling(handler: VoidCallback): T
```

Triggered when the inertial animation of the scrollable component ends. It is not triggered if the animation is interrupted by a new swipe gesture.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-ScrollableCommonMethod-onDidStopFling(handler: VoidCallback): T--><!--Device-ScrollableCommonMethod-onDidStopFling(handler: VoidCallback): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the inertial animation of the scrollable component ends. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onReachEnd

```TypeScript
onReachEnd(event: () => void): T
```

Triggered when the scrollable component reaches the end position.

Triggered once when the scrollable component is initialized and is already at the end position. When the edge effect is a spring effect, this event is triggered once when the component is swiped past the end position, and once again when it bounces back to the end position.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-onReachEnd(event: () => void): T--><!--Device-ScrollableCommonMethod-onReachEnd(event: () => void): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the scrollable component reaches the end position. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onReachStart

```TypeScript
onReachStart(event: () => void): T
```

Triggered when the scrollable component reaches the start position.

This event is triggered once when the component is initialized and once when the component scrolls to the start position. If the edge effect is set to a spring effect, this event is triggered once when the swipe passes the start position, and triggered again when the swipe rebounds back to the start position.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-onReachStart(event: () => void): T--><!--Device-ScrollableCommonMethod-onReachStart(event: () => void): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the scrollable component reaches the start position. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onScrollStart

```TypeScript
onScrollStart(event: () => void): T
```

Triggered when the scrollable component starts scrolling initiated by the user's finger dragging the component or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) starts.

Trigger conditions:

1. The scrollable component starts scrolling, supporting various input settings including keyboard and mouse
operations.
2. Scrolling is initiated through scroller controller API calls with transition animation effects.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-onScrollStart(event: () => void): T--><!--Device-ScrollableCommonMethod-onScrollStart(event: () => void): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when scrolling starts. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onScrollStop

```TypeScript
onScrollStop(event: () => void): T
```

Triggered when the scrollable component stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) stops.

Trigger conditions:

1. The scrollable component stops scrolling, supporting various input settings including keyboard and mouse
operations.
2. The animation stops after scroller controller API calls with transition effects.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-onScrollStop(event: () => void): T--><!--Device-ScrollableCommonMethod-onScrollStop(event: () => void): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when scrolling stops. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onWillScroll

```TypeScript
onWillScroll(handler: Optional<OnWillScrollCallback>): T
```

Triggered before the scrollable component scrolls. Comparison with [onDidScroll](#ondidscroll): **onWillScroll** is triggered before scrolling occurs and can specify the offset to be scrolled through its return value, making it suitable for scenarios where scrolling needs to be intercepted or customized; **onDidScroll **is triggered when scrolling occurs and returns the actual scroll offset and scrolling state of the current frame, making it suitable for scenarios where only the scrolling process needs to be monitored. The two can be used together.

Called to return the offset to be scrolled in the current frame, the current scroll state, and the source of the scroll operation. The offset returned in the callback is the calculated offset to be scrolled, not the final actual scroll offset. You can specify the offset to be scrolled by the scrollable component through the return value of this callback. The parameter type of the [onWillScroll](arkts-arkui-scroll-comp-attribute.md#onwillscroll) API of the [Scroll](arkts-arkui-scroll-comp.md) component is [ScrollOnWillScrollCallback](arkts-arkui-scroll-comp-scrollonwillscrollcallback-t.md).

> **NOTE:** 
> 
> - This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 14.
> 
> - When [ScrollEdge](arkts-arkui-scroll-comp-scroller-c.md#scrolledge) and [ScrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex) without animation are called, **onWillScroll** is not triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollableCommonMethod-onWillScroll(handler: Optional<OnWillScrollCallback>): T--><!--Device-ScrollableCommonMethod-onWillScroll(handler: Optional<OnWillScrollCallback>): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnWillScrollCallback](arkts-arkui-common-comp-onwillscrollcallback-t.md)&gt; | Yes | Callback triggered when the scrollable component is about to scroll. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onWillStartDragging

```TypeScript
onWillStartDragging(handler: VoidCallback): T
```

Triggered when the scrollable component starts to be dragged.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-ScrollableCommonMethod-onWillStartDragging(handler: VoidCallback): T--><!--Device-ScrollableCommonMethod-onWillStartDragging(handler: VoidCallback): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the scrollable component starts to be dragged. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onWillStartFling

```TypeScript
onWillStartFling(handler: VoidCallback): T
```

Triggered when the scrollable component is about to initiate an inertial animation.

> **NOTE:** 
> 
> - If the inertial animation is triggered by the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) method, **onWillStartFling** is not triggered.
> 
> - For details about the triggering scenarios of the inertial animation, see the description of [flingSpeedLimit](#flingspeedlimit).

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-ScrollableCommonMethod-onWillStartFling(handler: VoidCallback): T--><!--Device-ScrollableCommonMethod-onWillStartFling(handler: VoidCallback): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the scrollable component is about to initiate an inertial animation. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onWillStopDragging

```TypeScript
onWillStopDragging(handler: OnWillStopDraggingCallback): T
```

Triggered when the scrollable component is released. It is not triggered for scrolling via mouse wheel.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-ScrollableCommonMethod-onWillStopDragging(handler: OnWillStopDraggingCallback): T--><!--Device-ScrollableCommonMethod-onWillStopDragging(handler: OnWillStopDraggingCallback): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnWillStopDraggingCallback](arkts-arkui-common-comp-onwillstopdraggingcallback-t.md) | Yes | Callback invoked when the scrollable component is released. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## scrollBar

```TypeScript
scrollBar(barState: BarState): T
```

Sets the scrollbar state.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-scrollBar(barState: BarState): T--><!--Device-ScrollableCommonMethod-scrollBar(barState: BarState): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| barState | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Scrollbar state. **BarState.Off** indicates that the scrollbar is not displayed; **BarState.Auto** indicates that the scrollbar is displayed as needed; **BarState.On** indicates that the scrollbar is always displayed.<br>Default value: **BarState.Auto** for the **List**, **Grid**, and **Scroll** components, and **BarState.Off** for the **WaterFlow** component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string): T
```

Sets the scrollbar color.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string): T--><!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string | Yes | Scrollbar color.<br>The default value on children's smartwatches is **'#ffffff'**, which indicates white (100% opacity). The default value on other devices is **'#182431'**, which indicates dark blue-gray (40% opacity). <br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

<a id="scrollbarcolor-1"></a>

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource): T
```

Sets the scrollbar color. Compared with [scrollBarColor&lt;sup&gt;11+&lt;/sup&gt;](#scrollbarcolor), this API supports the Resource type for the **color** parameter.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string | Resource): T--><!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string | Resource): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar color.<br>The default value on children's smartwatches is **'#ffffff'**, which indicates white (100% opacity). The default value on other devices is **'#182431'**, which indicates dark blue-gray (40% opacity). <br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## scrollBarHeight

```TypeScript
scrollBarHeight(height: LengthMetrics | undefined): T
```

Sets the height of the scrollbar track.

If this API is not called, the height of the scrollbar track adapts to the height of the scrollable component by default. The default height on a wearable is 37 vp.

> **NOTE:** 
> 
> Ensure that the sum of the values set for **scrollBarHeight** and
> [scrollBarMargin](#scrollbarmargin)
> does not exceed the height of the scrollable component. Otherwise, the scrollbar may fail to display properly.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollableCommonMethod-scrollBarHeight(height: LengthMetrics | undefined): T--><!--Device-ScrollableCommonMethod-scrollBarHeight(height: LengthMetrics | undefined): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | LengthMetrics &#124; undefined | Yes | Height of the scrollbar track.<br>The value must be greater than or equal to 0. If it is set to **undefined** or a value less than 0, the height adapts to the scrollable component, and on a wearable it is restored to the default value 37 vp. If it is set to 0, the scrollbar is not displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## scrollBarMargin

```TypeScript
scrollBarMargin(margin: ScrollBarMargin): T
```

Sets the margin of the scrollbar. The margin is calculated based on the distance by which the scrollbar avoids the rounded corner area of the scrollable component. If the scrollbar area is smaller than the minimum length of the scrollbar, the scrollbar is not displayed. If this attribute is set, the automatic margin adjustment of [autoAdjustScrollBarMargin](#autoadjustscrollbarmargin) does not take effect. Ensure that the sum of [scrollBarHeight](#scrollbarheight) and the value of this attribute does not exceed the height of the scrollable component; otherwise, the scrollbar may not be displayed properly.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollableCommonMethod-scrollBarMargin(margin: ScrollBarMargin): T--><!--Device-ScrollableCommonMethod-scrollBarMargin(margin: ScrollBarMargin): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| margin | [ScrollBarMargin](../arkts-apis/arkts-arkui-scrollbarmargin-i.md) | Yes | Start and end margins of the scrollbar.<br>Default value for children's smartwatches: **{start: LengthMetrics.vp(42), end: LengthMetrics.vp(0)}**<br>Default value for other devices: **{start: LengthMetrics.vp(0), end: LengthMetrics.vp(0)}** |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string): T
```

Sets the width of the scrollbar. Percentage values are not supported. After the width is set, the scrollbar width in both the normal state and the pressed state is the set value. If the scrollbar width exceeds the visible size of the scrollable component along the main axis, the scrollbar width changes to the default value of 4 vp.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string): T--><!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Width of the scrollbar.<br>Default value: **4**<br>Unit: vp <br>Value range: [0, +∞). If the value is less than 0, the default value is used, and on a children's smartwatch, the default value 5 vp is restored. If the value is 0, the scrollbar is not displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

<a id="scrollbarwidth-1"></a>

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource): T
```

Sets the width of the scrollbar. Percentage values are not supported. After the width is set, the scrollbar width in both the normal state and the pressed state is the set value. If the scrollbar width exceeds the visible size of the scrollable component along the main axis, the scrollbar width changes to the default value of 4 vp. Resource type is supported.

If this API is not used, the scrollbar width is 4 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string | Resource): T--><!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string | Resource): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar width.<br>Unit: vp <br>The value range is [0, +∞). If this parameter is set to a value less than 0, **4vp** is used, and **5vp** is used for children's smartwatches. The value **0** means not to show the scrollbar. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T
```

Triggered when the scrollable component scrolls.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [onDidScroll](#ondidscroll)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollableCommonMethod-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T--><!--Device-ScrollableCommonMethod-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) =&gt; void | Yes | Callback triggered when the scrollable component scrolls.<br>**scrollOffset**: offset relative to the previous frame. The offset is positive when the scrollable component is scrolled up and negative when it is scrolled down. Unit: vp <br>**scrollState**: current scroll state. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current scrollable component. |
