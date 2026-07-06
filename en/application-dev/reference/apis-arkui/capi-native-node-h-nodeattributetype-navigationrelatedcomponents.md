# ArkUI_NodeAttributeType (Navigation Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for navigation components including **Swiper**.

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
| .value[0].i32 | Whether loop playback is enabled. The value **1** means that loop playback is enabled, and **0** means the opposite. The default value is **1**.|

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
| .value[0].i32 | Whether automatic playback is enabled for child component switching. The value **1** means that automatic playback is enabled, and **0** means the opposite. The default value is **0**.|
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
| .value[0].i32 | Whether the navigation indicator is shown. The value **1** means that the navigation indicator is shown, and **0** means the opposite. The default value is **1**.|

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
| .value[0].f32 | Interval for automatic playback, in ms.|

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
| .value[0].i32 | Whether vertical swiping is used. The value **1** means that vertical swiping is used, and **0** means that horizontal swiping is used. The default value is **0**.|

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
| .value[0].f32 | Duration of the animation for switching child components, in milliseconds. The default value is **400**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Duration of the animation for switching child components, in milliseconds. The default value is **400**.|

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
| .value[0].i32 | Animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is **ARKUI_CURVE_LINEAR**.|

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
| .value[0].f32 | Spacing between child components.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Spacing between child components.|

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
| .value[0].i32 | Index of the child component.|
| .value[1]?.i32 | Switching animation mode. The parameter type is [ArkUI_SwiperAnimationMode](capi-swiper-h.md#arkui_swiperanimationmode). The setting is only effective for the current call.<br>This parameter is supported since API version 15.|

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
| .value[0].i32 | Number of elements to display per page.|
| .value[1]?.i32 | Whether to paginate by group. The value **0** means to paginate by elements, and **1** means to paginate by groups of elements displayed within the viewport. The default value is **0**.|
| .string? | Whether to enable auto-adaptation. This parameter accepts only the value **"auto"**. When this parameter is set to **"auto"**, the **value[]** parameters are ignored.<br>This parameter is supported since API version 19.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of elements to display per page.|
| .value[1].i32 | Whether pagination by group is enabled. This parameter is supported since API version 19.|

## NODE_SWIPER_DISABLE_SWIPE

```c
NODE_SWIPER_DISABLE_SWIPE = 1001010
```

Whether to disable the swipe-to-switch feature of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to disable the swipe-to-switch feature. The value **1** means to disable the feature, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the swipe-to-switch feature is disabled. The value **1** means that the feature is disabled, and **0** means the opposite. The default value is **0**.|

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
| .?object | Style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the arrow is shown when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow).|
| .object | Style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.|

## NODE_SWIPER_EDGE_EFFECT_MODE

```c
NODE_SWIPER_EDGE_EFFECT_MODE = 1001012
```

Effect used at the edges of the **Swiper** component when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).<br>The default value is **ARKUI_EDGE_EFFECT_SPRING**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).|

## NODE_SWIPER_NODE_ADAPTER

```c
NODE_SWIPER_NODE_ADAPTER = 1001013
```

Adapter of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter.|

**Returns**

| Type| Description|
| -- | -- |
| .object | [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object.|

## NODE_SWIPER_CACHED_COUNT

```c
NODE_SWIPER_CACHED_COUNT = 1001014
```

Number of cached items in the **Swiper** component's adapter. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of cached items in the **Swiper** component's adapter.|
| .value[1]?.i32 | Whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. The default value is **0**. This parameter is supported since API version 19.|
| .value[2]?.i32 | Whether to calculate the number of cached items by group. That is, the number of preloaded child components is calculated by group. **1**: The actual number of cached items is used. **0**: When **NODE_SWIPER_DISPLAY_COUNT** is set to page switching by group, the number of cached items is calculated by group. If **NODE_SWIPER_DISPLAY_COUNT** is not set, the actual number of cached items is used. The default value is **0**. This parameter is supported since API version 24.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of cached items in the adapter.|
| .value[1].i32 | Whether cached items are shown. The value **0** means that cached items are hidden, and **1** means that cached items are shown. This parameter is supported since API version 19.|
| .value[2].i32 | Whether the number of cached items is calculated by group. This parameter is supported since API version 24. \n |

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
| .value[0].f32 | Leading margin, in vp. The default value is **0**.|
| .value[1]?.i32 | Whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Leading margin, in vp.|
| .value[1].i32 | Whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.|

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
| .value[0].f32 | Trailing margin, in vp. The default value is **0**.|
| .value[1]?.i32 | Whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Trailing margin, in vp.|
| .value[1].i32 | Whether to ignore blank areas. The value **1** means to ignore blank areas, and **0** means the opposite.|

## NODE_SWIPER_INDICATOR

```c
NODE_SWIPER_INDICATOR = 1001017
```

Navigation indicator type of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype).|
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

Nested scrolling mode of the **Swiper** component and its parent component.<br>
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

Sets the **Swiper** component to switch to the specified page.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Index of the target page in the **Swiper** component.|
| .value[1]?.i32 | Whether to use an animation when the target page is reached. The value **1** indicates to use the animation, and the value **0** indicates not to use the animation. The default value is **0**.|

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
| .value[0].i32 | Page flipping mode using the mouse wheel.|

## NODE_SWIPER_AUTO_FILL

```c
NODE_SWIPER_AUTO_FILL = 1001022
```

Configures the **Swiper** component to automatically adjust the number of elements displayed per page based on the minimum width of the elements. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum width of the elements to be displayed, in vp.|
| .value[1]?.i32 | Whether to paginate by group. The value **0** means to paginate by elements, and **1** means to paginate by groups of elements displayed within the viewport. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum width of the elements to be displayed, in vp.|
| .value[1].i32 | Whether pagination by group is enabled.|

## NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION

```c
NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023
```

Whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **Swiper** component.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to maintain the visible content's position when data is inserted or deleted outside the display area of the **Swiper** component. The value **1** means to maintain the visible content's position, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the visible content's position is maintained when data is inserted or deleted outside the display area of the **Swiper** component. The value **1** means that the visible content's position is maintained, and **0** means the opposite. The default value is **0**.|

## NODE_SWIPER_ITEMFILLPOLICY

```c
NODE_SWIPER_ITEMFILLPOLICY = 1001024
```

Responsive column layout policy of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
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
