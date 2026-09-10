# ArkUI_NodeAttributeType (Navigation Component Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=0db97a5b7fb8643c5f5eff515ac260c481581357 translatedAt=2026-08-25T02:22:56.719Z pushedAt=2026-08-26T09:08:15.385Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for navigation components including **Swiper** (swipe container component), **ArcSwiper**, and **ArcAlphabetIndexer** components. Among them, **Swiper** attributes are used to set carousel capabilities such as looping playback, autoplay, navigation indicators, and animation effects; **ArcSwiper** attributes are used to set the current index, navigation dot indicator, swipe direction, and edge effect of the arc swipe container; **ArcAlphabetIndexer** attributes are used to set the index array, color, font, pop-up window, and selected item of the arc alphabet indexer.

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
| .value[1]?.i32 | Whether to stop automatic playback when the user touches the screen. The value **1** means to stop automatic playback, and **0** means the opposite. The default value is **1**. This parameter is supported since API version 16. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether automatic playback is enabled for child component switching. The value **1** indicates automatic playback is enabled for child component switching, and **0** indicates the opposite.|
| .value[1].i32 | Whether automatic playback is stopped when the user touches the screen. The value **1** means that automatic playback is stopped, and **0** means the opposite. This parameter is supported since API version 16. |

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
**NODE_SWIPER_AUTO_PLAY** must be set to **1** (enable auto-play) first for the time interval set by this attribute to take effect.<br/>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Interval for automatic playback, in milliseconds. The value range is [0, +∞). The default value is **3000**. |

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

Animation curve for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. If this attribute is not set or reset, the animation curve is [interpolatingSpring](../../reference/apis-arkui/js-apis-curve.md#curvesinterpolatingspring10)(-1, 1, 328, 34). If an exception occurs (such as mismatching parameter type or invalid parameter) when setting this attribute, the default value **ARKUI_CURVE_LINEAR** is used.<br>

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is **ARKUI_CURVE_LINEAR**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). |

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
| .value[1]?.i32 | Swipe animation mode. The parameter type is [ArkUI_SwiperAnimationMode](capi-swiper-h.md#arkui_swiperanimationmode). The default value is **ARKUI_SWIPER_ANIMATION_MODE_NONE**. It is effective only for this setting.<br>This parameter is supported since API version 15. |

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
| .value[1]?.i32 | Whether to paginate by group. The value **0** means to paginate by elements, and **1** means to paginate by groups of elements displayed within the viewport. The default value is **0**. This parameter is supported since API version 19. |
| .string? | Whether to enable auto-adaptation. This parameter accepts only the value **"auto"**. When this parameter is set to **"auto"**, the **value[]** parameters are ignored. If this parameter is not set, the **value[]** parameter is used.<br>This parameter is supported since API version 19. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of elements to display per page.|
| .value[1].i32 | Whether pagination by group is enabled. The value **0** indicates that pagination is performed by elements, and **1** indicates that pagination is performed by groups of elements displayed within the viewport. This parameter is supported since API version 19.|
| .string | The value **auto** indicates the number of elements to display after being automatically adjusted. This parameter is supported since API version 19.|

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
| .value[0].i32 | Whether to show the arrow when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow). The default value is **ARKUI_SWIPER_ARROW_HIDE**. |
| ?.object | Style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). If this parameter is not set, the default arrow style is used.<br>This parameter is supported since API version 19.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the arrow is shown when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow). |
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
| .value[0].i32 | Effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). |

## NODE_SWIPER_NODE_ADAPTER

```c
NODE_SWIPER_NODE_ADAPTER = 1001013
```

Adapter of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. The adapter is used when the **Swiper** component needs to dynamically load or reuse child components, for example, list carousel with a large amount of data and carousel with an infinite loop.

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md) object used as the adapter. You are advised to use this parameter together with **NODE_SWIPER_CACHED_COUNT** to improve performance. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Adapter object. The parameter type is [ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md), used to dynamically load or reuse **Swiper** child components. |

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
| .value[0].i32 | Number of cached items in the adapter of **Swiper**. The value range is [0, +∞). The default value is **1**. You are advised to set this parameter based on the actual service scenario to avoid high memory usage. |
| .value[1]?.i32 | Whether to show cached items. The value **0** means to hide cached items, and **1** means to show cached items. The default value is **0**. This parameter is supported since API version 19.|
| .value[2]?.i32 | Whether the number of cached items is calculated by group. The value **0** indicates that the number of cached items is calculated by group when **NODE_SWIPER_DISPLAY_COUNT** is set to pagination by group. The value **1** indicates that the actual number of cached items is used. The default value is **0**. This parameter is supported since API version 24.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of cached items in the adapter of **Swiper**. |
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
| .value[1].i32 | Whether blank areas are ignored. The value **1** indicates blank areas are ignored, and **0** indicates the opposite. |

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
| .value[0].i32 | Navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype). |
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
| .value[0].i32 | Nested scrolling mode of the **Swiper** component and its parent component. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode). It takes effect only when the **Swiper** component is nested in a scrollable container. Default value: **ARKUI_SWIPER_NESTED_SCROLL_SELF_ONLY**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Nested scrolling mode. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode). |

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

Page flipping mode using the mouse wheel. This attribute can be set, reset, and obtained as required through APIs.<br>

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode). The default value is **ARKUI_PAGE_FLIP_MODE_CONTINUOUS**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode). |

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
| .value[0].f32 | Minimum width of the elements, in vp.|
| .value[1].i32 | Whether pagination by group is enabled. The value **0** indicates that pagination is performed by elements, and **1** indicates that pagination is performed by groups of elements displayed within the viewport. |

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
| .value[0].i32 | Responsive layout policy. The parameter type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy). |
| .value[1].i32 | Whether pagination by group is enabled. The value **0** indicates that pagination is performed by elements, and **1** indicates that pagination is performed by groups of elements displayed within the viewport. |

## NODE_ARC_ALPHABET_INDEXER_ARRAY

```c
NODE_ARC_ALPHABET_INDEXER_ARRAY = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_ALPHABET_INDEXER = 23000
```

Index string array. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .object | Index string array. |

**Returns**

| Type | Description |
| -- | -- |
| .object | Index string array. |

## NODE_ARC_ALPHABET_INDEXER_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_COLOR = 23001
```

Text color of the index item in the unselected state. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].u32 | Text color, in 0xARGB format. The default value is **0xFFFFFFFF**, which indicates white. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].u32 | Text color, in 0xARGB format. |

## NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR = 23002
```

Text color of the index item in the selected state. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].u32 | Text color, in 0xARGB format. The default value is **0xFFFFFFFF**, which indicates white. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].u32 | Text color, in 0xARGB format. |

## NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR = 23003
```

Text color of the popup. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].u32 | Text color, in 0xARGB format. The default value is **0xFFFFFFFF**, which indicates white. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].u32 | Text color, in 0xARGB format. |

## NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR = 23004
```

Background color of the index item in the selected state. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. The default value is **0xFF1F71FF**, which indicates blue. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. |

## NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR = 23005
```

Background color of the popup. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. The default value is **0xD8404040**, which indicates dark gray. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. |

## NODE_ARC_ALPHABET_INDEXER_USE_POPUP

```c
NODE_ARC_ALPHABET_INDEXER_USE_POPUP = 23006
```

Whether to use the popup. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to use the popup. The value **1** indicates to use the popup, and **0** indicates the opposite. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the popup is used. |

## NODE_ARC_ALPHABET_SELECTED_FONT

```c
NODE_ARC_ALPHABET_SELECTED_FONT = 23007
```

Font style of the selected index item. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .string | Font family. Multiple fonts are separated by comma (,). This is an optional parameter. The default value is **"HarmonyOS Sans"**. |
| .value[0].f32 | Font size, in fp. This is an optional parameter. The default value is **13**. |
| .value[1].i32 | Font weight. This is an optional parameter. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_W500**. |
| .value[2].i32 | Font style. This is an optional parameter. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**. |

**Returns**

| Type | Description |
| -- | -- |
| .string | Font family. Multiple fonts are separated by comma (,). |
| .value[0].f32 | Font size, in fp. |
| .value[1].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). |
| .value[2].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). |

## NODE_ARC_ALPHABET_INDEXER_POPUP_FONT

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_FONT = 23008
```

Font style of the popup. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .string | Font family. Multiple fonts are separated by comma (,). This is an optional parameter. The default value is **"HarmonyOS Sans"**. |
| .value[0].f32 | Font size, in fp. This is an optional parameter. The default value is 19. |
| .value[1].i32 | Font weight. This is an optional parameter. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_W500**. |
| .value[2].i32 | Font style. This is an optional parameter. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**. |

**Returns**

| Type | Description |
| -- | -- |
| .string | Font family. Multiple fonts are separated by comma (,). |
| .value[0].f32 | Font size, in fp. |
| .value[1].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). |
| .value[2].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). |

## NODE_ARC_ALPHABET_FONT

```c
NODE_ARC_ALPHABET_FONT = 23009
```

Default font style of the index item. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .string | Font family. Multiple fonts are separated by comma (,). This is an optional parameter. The default value is **"HarmonyOS Sans"**. |
| .value[0].f32 | Font size, in fp. This is an optional parameter. The default value is **13**. |
| .value[1].i32 | Font weight. This is an optional parameter. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_W500**. |
| .value[2].i32 | Font style. This is an optional parameter. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**. |

**Returns**

| Type | Description |
| -- | -- |
| .string | Font family. Multiple fonts are separated by comma (,). |
| .value[0].f32 | Font size, in fp. |
| .value[1].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). |
| .value[2].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). |

## NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE

```c
NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE = 23010
```

Size of the letter area of the alphabet index bar. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].f32 | Diameter of the circle when the letter area is circular, in vp. The default value is **24**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].f32 | Diameter of the circle when the letter area is circular, in vp. |

## NODE_ARC_ALPHABET_INDEXER_SELECTED

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED = 23011
```

Index of the selected item. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Index of the selected item. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Index of the selected item. |

## NODE_ARC_ALPHABET_AUTO_COLLAPSE

```c
NODE_ARC_ALPHABET_AUTO_COLLAPSE = 23012
```

Whether to collapse the characters when the space of the index bar is insufficient to display all characters. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to collapse the characters when the space of the index bar is insufficient to display all characters. The value **1** indicates to collapse the characters, and **0** indicates the opposite. The default value is **1**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the characters are collapsed when the space of the index bar is insufficient to display all characters. |

## NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE

```c
NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE = 23013
```

Background blur style of the popup. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Background blur style of the popup. The parameter type is [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle). The default value is **ARKUI_BLUR_STYLE_NONE**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Background blur style of the popup. |

## NODE_ARC_SWIPER_INDEX

```c
NODE_ARC_SWIPER_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SWIPER = 1022000
```

Index of the child component currently displayed in the **ArcSwiper** container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Index of the child component. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Index of the child component. |

## NODE_ARC_SWIPER_INDICATOR

```c
NODE_ARC_SWIPER_INDICATOR = 1022001
```

Navigation dot indicator of the **ArcSwiper** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to display the navigation dot indicator. The value **1** indicates to display, and **0** indicates the opposite. The default value is **1**. |
| .value[1].i32 | Direction of the **ArcSwiper** navigation dot indicator. The parameter type is [OH_ArkUI_ArcDirection](capi-native-type-h.md#oh_arkui_arcdirection). The default value is **OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION**. This is an optional parameter. |
| .value[2].i32 | Color of the unselected dot, in 0xARGB format. The default value is **0xA9FFFFFF**, which indicates white. This is an optional parameter. |
| .value[3].i32 | Color of the selected dot, in 0xARGB format. The default value is **0xFF5EA1FF**, which indicates blue. This is an optional parameter. |
| .value[4].i32 | Background color of the **ArcSwiper** navigation dot indicator after a long press, in 0xARGB format. The default value is **0xFF5EA1FF**, which indicates blue. This is an optional parameter. |
| .object | Gradient color of the mask. This is an optional parameter. In a color stop array, each color stop consists of a color and its stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. **colors**: color of the color stop. **stops**: stop of the color. **size**: number of colors. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the navigation dot indicator is displayed. |
| .value[1].i32 | Direction of the **ArcSwiper** navigation dot indicator. |
| .value[2].u32 | Color of the unselected dot. |
| .value[3].u32 | Color of the selected dot. |
| .value[4].u32 | Background color of the **ArcSwiper** navigation dot indicator after a long press. |
| .object | Gradient color of the mask. |

## NODE_ARC_SWIPER_DURATION

```c
NODE_ARC_SWIPER_DURATION = 1022002
```

Animation duration for child component switching. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Animation duration for child component switching, in milliseconds. The value range is [0, +∞). When not set, the default value is **400**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Animation duration for child component switching, in milliseconds. |

## NODE_ARC_SWIPER_VERTICAL

```c
NODE_ARC_SWIPER_VERTICAL = 1022003
```

Whether to use vertical swiping. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to use vertical swiping. The value **1** indicates to use vertical swiping, and **0** indicates to use horizontal swiping. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether vertical swiping is used. |

## NODE_ARC_SWIPER_DISABLE_SWIPE

```c
NODE_ARC_SWIPER_DISABLE_SWIPE = 1022004
```

Whether to disable swiping. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to disable swiping. The value **1** indicates to disable, and **0** indicates the opposite. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether swiping is disabled. |

## NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY

```c
NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY = 1022005
```

Sensitivity of rotating the digital crown. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Sensitivity of rotating the digital crown. The parameter type is [ArkUI_CrownSensitivity](capi-native-type-h.md#arkui_crownsensitivity). The default value is **ARKUI_CROWN_SENSITIVITY_MEDIUM**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Sensitivity of rotating the digital crown. |

## NODE_ARC_SWIPER_EFFECT_MODE

```c
NODE_ARC_SWIPER_EFFECT_MODE = 1022006
```

Edge swipe effect of the **ArcSwiper** component when swiping to the boundary of the scrollable content. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Edge swipe effect of the **ArcSwiper** component when swiping to the boundary of the scrollable content. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is **ARKUI_EDGE_EFFECT_SPRING**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Edge swipe effect of the **ArcSwiper** component when swiping to the boundary of the scrollable content. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). |

## NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION

```c
NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION = 1022007
```

Whether to disable the transition animation. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| .value[0].i32 | Whether to disable the transition animation. The value **1** indicates to disable, and **0** indicates the opposite. The default value is **0**. |

**Returns**

| Type | Description |
| -- | -- |
| .value[0].i32 | Whether the transition animation is disabled. |