# ArkUI_NodeAttributeType (Navigation Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for navigation components including **Swiper**. These attribute types cover the core features of the **Swiper** component, such as loop playback, auto-play, navigation indicator, and animation effect. You can combine them as required to achieve different carousel effects.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_SWIPER_LOOP

```c
NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER = 1001000
```

Whether to enable loop playback for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable loop playback. The value **1** means to enable loop playback, and **0** means the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether loop playback is enabled. The value **1** indicates loop playback is enabled, and **0** indicates the opposite.|

## NODE_SWIPER_AUTO_PLAY

```c
NODE_SWIPER_AUTO_PLAY = 1001001
```

Whether to enable automatic playback for child component switching in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable automatic playback for child component switching. The value **1** means to enable automatic playback, and **0** means the opposite. The default value is **0**.|
| .value[1]?.i32 | Whether to stop automatic playback when the user touches the screen. The value **0** means to stop automatic playback, and **1** means the opposite. The default value is **0**. This parameter is supported since API version 16.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether automatic playback is enabled for child component switching. The value **1** indicates automatic playback is enabled for child component switching, and **0** indicates the opposite.|
| .value[1].i32 | Whether automatic playback is stopped when the user touches the screen. The value **0** means that automatic playback is stopped, and **1** means the opposite. This parameter is supported since API version 16.|

## NODE_SWIPER_SHOW_INDICATOR

```c
NODE_SWIPER_SHOW_INDICATOR = 1001002
```

Whether to show the navigation indicator for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show the navigation indicator. The value **1** means to show the navigation indicator, and **0** means the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the navigation indicator is shown. The value **1** indicates the navigation indicator is shown, and **0** indicates the opposite.|

## NODE_SWIPER_INTERVAL

```c
NODE_SWIPER_INTERVAL = 1001003
```

Interval for automatic playback in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Interval for automatic playback, in milliseconds. The value range is [0, +∞).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Interval for automatic playback, in ms.|

## NODE_SWIPER_VERTICAL

```c
NODE_SWIPER_VERTICAL = 1001004
```

Whether to use vertical swiping for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to use vertical swiping. The value **1** means to use vertical swiping, and **0** means to use horizontal swiping. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether vertical swiping is used. The value **1** indicates vertical sliding is used, and **0** indicates horizontal sliding is used.|

## NODE_SWIPER_DURATION

```c
NODE_SWIPER_DURATION = 1001005
```

Duration of the animation for switching child components in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Duration of the animation for switching child components, in milliseconds. The value range is [0, +∞). The default value is **400**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Duration of the animation for switching child components, in milliseconds.|

## NODE_SWIPER_CURVE

```c
NODE_SWIPER_CURVE = 1001006
```

Animation curve for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. If this attribute is not set or reset, the animation curve is [interpolatingSpring](../../reference/apis-arkui/js-apis-curve.md#curvesinterpolatingspring10)(-1, 1, 328, 34). If an exception occurs when setting this attribute, the default value **ARKUI_CURVE_LINEAR** is used.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is **ARKUI_CURVE_LINEAR**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).|

## NODE_SWIPER_ITEM_SPACE

```c
NODE_SWIPER_ITEM_SPACE = 1001007
```

Spacing between child components in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components, in vp. The value range is [0, +∞), and the default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components, in vp.|

## NODE_SWIPER_INDEX

```c
NODE_SWIPER_INDEX = 1001008
```

Index of the child component currently displayed in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Index of the child component. The value range is [0, Number of child components – 1]. The default value is **0**.|
| .value[1]?.i32 | Switching animation mode. The parameter type is [ArkUI_SwiperAnimationMode](capi-swiper-h.md#arkui_swiperanimationmode). The default value is no animation mode. The setting is only effective for the current call.<br>This parameter is supported since API version 15.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Index of the child component.|

## NODE_SWIPER_DISPLAY_COUNT

```c
NODE_SWIPER_DISPLAY_COUNT = 1001009
```

Number of elements to display per page for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of elements to display per page. The value range is [1, +∞). The default value is **1**.|
| .value[1]?.i32 | Whether to paginate by group. The value **0** means to paginate by elements, and **1** means to paginate by groups of elements displayed within the viewport. The default value is **0**.|
| .string? | Whether to enable auto-adaptation. This parameter accepts only the value **"auto"**. When this parameter is set to **"auto"**, the **value[]** parameters are ignored. If this parameter is not set, the **value[]** parameter is used.<br>This parameter is supported since API version 19.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of elements to display per page.|
| .value[1].i32 | Whether pagination by group is enabled. The value **0** indicates that pagination is performed by elements, and **1** indicates that pagination is performed by groups of elements displayed within the viewport. This parameter is supported since API version 19.|
| .string | The value **auto** indicates that the number of elements to display after being automatically adjusted. This parameter is supported since API version 19.|

## NODE_SWIPER_DISABLE_SWIPE

```c
NODE_SWIPER_DISABLE_SWIPE = 1001010
```

Whether to disable the swipe-to-switch feature of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. For example, you can disable the swipe-to-switch feature to allow page switching only through navigation arrows or indicators, or to prevent gesture sliding interference.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to disable the swipe-to-switch feature. The value **1** means to disable the feature, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the swipe-to-switch feature is disabled. The value **1** indicates the swipe-to-switch feature is disabled, and **0** indicates the opposite.|

## NODE_SWIPER_SHOW_DISPLAY_ARROW

```c
NODE_SWIPER_SHOW_DISPLAY_ARROW = 1001011
```

Whether to show the arrow when the mouse pointer hovers over the navigation indicator in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show the arrow when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow). The default value is **ARKUI_SWIPER_ARROW_HIDE**.|
| ?.object | Style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). If this parameter is not set, the default arrow style is used.<br>This parameter is supported since API version 19.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the arrow is shown when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow).|
| .object | Style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.|

## NODE_SWIPER_EDGE_EFFECT_MODE

```c
NODE_SWIPER_EDGE_EFFECT_MODE = 1001012
```

Effect used at the edges of the **Swiper** component when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs. When the **Swiper** component has reached the first or last child component, the edge effect is triggered if the user continues to slide.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is **ARKUI_EDGE_EFFECT_SPRING**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).|

## NODE_SWIPER_NODE_ADAPTER

```c
NODE_SWIPER_NODE_ADAPTER = 1001013
```

Adapter of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. The adapter is used when the **Swiper** component needs to dynamically load or reuse child components, for example, list carousel with a large amount of data and carousel with an infinite loop.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter. You are advised to use this parameter together with **NODE_SWIPER_CACHED_COUNT** to improve performance.|

**Returns**

| Type| Description|
| -- | -- |
| .object | [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object.|

## NODE_SWIPER_CACHED_COUNT

```c
NODE_SWIPER_CACHED_COUNT = 1001014
```

Number of cached items in the adapter of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used to optimize the **Swiper** performance. When the rendering of child components is complex or more pages need to be preloaded, you can increase the number of cached items.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of cached items in the adapter of **Swiper**. The value range is [0, +∞). You are advised to set this parameter based on the actual service scenario to avoid high memory usage.|
| .value[1]?.i32 | Whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. The default value is **0**. This parameter is supported since API version 19.|
| .value[2]?.i32 | Whether the number of cached items is calculated by group. The value **0** indicates that the number of cached items is calculated by group when **NODE_SWIPER_DISPLAY_COUNT** is set to pagination by group. The value **1** indicates that the actual number of cached items is used. The default value is **0**. This parameter is supported since API version 24.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of cached items in the adapter of **Swiper**.|
| .value[1].i32 | Whether cached items are shown. The value **0** means cached items are hidden, and **1** means cached items are shown. This parameter is supported since API version 19.|
| .value[2].i32 | Whether the number of cached items is calculated by group. The value **0** means the number of cached items is calculated by group, and **1** means the actual number of cached items is used. This parameter is supported since API version 24.|

## NODE_SWIPER_PREV_MARGIN

```c
NODE_SWIPER_PREV_MARGIN = 1001015
```

Leading margin of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Leading margin, in vp. The value range is [0, +∞). The default value is **0**.|
| .value[1]?.i32 | Whether to ignore blank areas. The value **1** indicates to ignore blank areas, and **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Leading margin, in vp.|
| .value[1].i32 | Whether blank areas are ignored. The value **1** indicates blank areas are ignored, and **0** indicates the opposite. The default value is **0**.|

## NODE_SWIPER_NEXT_MARGIN

```c
NODE_SWIPER_NEXT_MARGIN = 1001016
```

Trailing margin of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Trailing margin, in vp. The value range is [0, +∞). The default value is **0**.|
| .value[1]?.i32 | Whether to ignore blank areas. The value **1** indicates to ignore blank areas, and **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Trailing margin, in vp.|
| .value[1].i32 | Whether blank areas are ignored. The value **1** indicates blank areas are ignored, and **0** indicates the opposite. The default value is **0**.|

## NODE_SWIPER_INDICATOR

```c
NODE_SWIPER_INDICATOR = 1001017
```

Navigation indicator type of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. **ARKUI_SWIPER_INDICATOR_TYPE_DOT** is applicable to scenarios such as carousel images and ad slots. **ARKUI_SWIPER_INDICATOR_TYPE_DIGIT** is applicable to scenarios where the current page number needs to be displayed, such as readers and galleries.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype). The default value is **ARKUI_SWIPER_INDICATOR_TYPE_DOT**.|
| .object | Additional configuration for the navigation indicator, depending on the type. For **ARKUI_SWIPER_INDICATOR_TYPE_DOT**, the parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md).<br>For **ARKUI_SWIPER_INDICATOR_TYPE_DIGIT**, the parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md).<br>The **ArkUI_SwiperDigitIndicator** type is supported since API version 19.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype).|
| .object | Additional configuration for the navigation indicator, depending on the type. For **ARKUI_SWIPER_INDICATOR_TYPE_DOT**, the parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md).<br>For **ARKUI_SWIPER_INDICATOR_TYPE_DIGIT**, the parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md).<br>The **ArkUI_SwiperDigitIndicator** type is supported since API version 19.|

## NODE_SWIPER_NESTED_SCROLL

```c
NODE_SWIPER_NESTED_SCROLL = 1001018
```

Nested scrolling mode of the **Swiper** component and its parent component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when **Swiper** is nested in scrollable containers such as **ScrollView** and **List**, to coordinate scrolling behavior and avoid scrolling conflicts.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Nested scrolling mode of the **Swiper** component and its parent component. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode).<br>The default value is **ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Nested scrolling mode of the **Swiper** component and its parent component. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode).|

## NODE_SWIPER_SWIPE_TO_INDEX

```c
NODE_SWIPER_SWIPE_TO_INDEX = 1001019
```

Sets the **Swiper** component to switch to the specified page. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows. This attribute cannot be reset or obtained through APIs.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Index of the target page in the Swiper component. The value range is [0, Number of pages – 1].|
| .value[1]?.i32 | Whether to use an animation when the target page is reached. The value **1** indicates to use the animation, and **0** indicates the opposite. The default value is **0**.|

## NODE_SWIPER_INDICATOR_INTERACTIVE

```c
NODE_SWIPER_INDICATOR_INTERACTIVE = 1001020
```

Whether the navigation indicator of a component is interactive.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the navigation indicator of a component is interactive. The value **1** indicates that the navigation indicator is interactive, and **0** indicates the opposite. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the navigation indicator of a component is interactive. The value **1** indicates that the navigation indicator is interactive, and **0** indicates the opposite.|

## NODE_SWIPER_PAGE_FLIP_MODE

```c
NODE_SWIPER_PAGE_FLIP_MODE = 1001021
```

Page flipping mode using the mouse wheel.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode) are as follows.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode).|

## NODE_SWIPER_AUTO_FILL

```c
NODE_SWIPER_AUTO_FILL = 1001022
```

Configures the **Swiper** component to automatically adjust the number of elements displayed per page based on the minimum width of the elements. This attribute can be set, reset, and obtained as required through APIs. This attribute is applicable to responsive layout. It is used when the number of elements displayed per page needs to be automatically adjusted based on the container width, such as in landscape mode or multi-device adaptation scenarios.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum width of the elements, in vp. The value range is (0, +∞).|
| .value[1]?.i32 | Whether to paginate by group. The value **0** means to paginate by elements, and **1** means to paginate by groups of elements displayed within the viewport. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum width of the elements to be displayed, in vp.|
| .value[1].i32 | Whether pagination by group is enabled. The value **0** indicates that pagination is performed by elements, and **1** indicates that pagination is performed by groups of elements displayed within the viewport.|

## NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION

```c
NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023
```

Whether to maintain the visible content's position when a child component is inserted or deleted outside the display area of the **Swiper** component. This attribute can be used to maintain the content currently displayed when a child component is dynamically added or deleted in **Swiper**, for example, in the chat record list and offering list.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to maintain the visible content's position when a child component is inserted or deleted outside the display area of the **Swiper** component. The value **1** indicates to maintain the visible content's position, and **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the visible content's position is maintained when a child component is inserted or deleted outside the display area of the **Swiper** component. The value **1** indicates that the visible content's position is maintained, and **0** indicates the opposite.|

## NODE_SWIPER_ITEMFILLPOLICY

```c
NODE_SWIPER_ITEMFILLPOLICY = 1001024
```

Responsive layout policy of the **Swiper** component, used to automatically adjust the number of child component columns displayed on a page based on different breakpoint specifications. This attribute can be set, reset, and obtained as required through APIs. This attribute is used to adaptively adjust the number of columns displayed on each page based on different screen sizes, such as in landscape mode or multi-device adaptation scenarios.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of columns at different breakpoint specifications. The parameter type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).|
| .value[1]?.i32 | Whether to paginate by group. The value **0** means to paginate by elements, and **1** means to paginate by groups of elements displayed within the viewport. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of columns at different breakpoint specifications. The parameter type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).|
| .value[1].i32 | Whether pagination by group is enabled.|
