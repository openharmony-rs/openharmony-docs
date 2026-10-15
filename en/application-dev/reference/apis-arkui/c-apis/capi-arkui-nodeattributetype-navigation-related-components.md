# Navigation Related Components

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_ARC_ALPHABET_INDEXER_ARRAY

```c
NODE_ARC_ALPHABET_INDEXER_ARRAY = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_ALPHABET_INDEXER
```

**Description**

Defines the index string array. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: array of the alphabet index. the type is string array.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: array of the alphabet index. the type is string array.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_COLOR
```

**Description**

Defines the text color of the index item in the unselected state. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: text color, in 0xARGB format. The default value is <b>0xFFFFFFFF</b>, which indicates white.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: text color, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR
```

**Description**

Defines the text color of the index item in the selected state. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: text color, in 0xARGB format. The default value is <b>0xFFFFFFFF</b>, which indicates white.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: text color, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR
```

**Description**

Defines the text color of the popup. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: text color, in 0xARGB format. The default value is <b>0xFFFFFFFF</b>, which indicates white.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: text color, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR
```

**Description**

Defines the background color of the index item in the selected state. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format. The default value is <b>0xFF1F71FF</b>, which indicates blue.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR
```

**Description**

Defines the background color of the popup. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format. The default value is <b>0xD8404040</b>, which indicates dark gray.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_USE_POPUP

```c
NODE_ARC_ALPHABET_INDEXER_USE_POPUP
```

**Description**

Defines whether to use the popup. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to use the popup. The value <b>1</b> indicates to use the popup, and <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the popup is used.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_SELECTED_FONT

```c
NODE_ARC_ALPHABET_SELECTED_FONT
```

**Description**

Defines the font style of the selected index item. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font family. Multiple fonts are separated by comma (,). This is an optional parameter. The default value is <b>"HarmonyOS Sans"</b>.</li> <li>.value[0].f32: font size, in fp. This is an optional parameter. The default value is <b>13</b>.</li> <li>.value[1].i32: font weight. This is an optional parameter. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_W500</b>.</li> <li>.value[2].i32: font style. This is an optional parameter. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Multiple fonts are separated by comma (,).</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_POPUP_FONT

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_FONT
```

**Description**

Defines the font style of the popup. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font family. Multiple fonts are separated by comma (,). This is an optional parameter. The default value is <b>"HarmonyOS Sans"</b>.</li> <li>.value[0].f32: font size, in fp. This is an optional parameter. The default value is <b>19</b>.</li> <li>.value[1].i32: font weight. This is an optional parameter. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_W500</b>.</li> <li>.value[2].i32: font style. This is an optional parameter. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Multiple fonts are separated by comma (,).</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_FONT

```c
NODE_ARC_ALPHABET_FONT
```

**Description**

Defines the default font style of the index item. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font family. Multiple fonts are separated by comma (,). This is an optional parameter. The default value is <b>"HarmonyOS Sans"</b>.</li> <li>.value[0].f32: font size, in fp. This is an optional parameter. The default value is <b>13</b>.</li> <li>.value[1].i32: font weight. This is an optional parameter. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_W500</b>.</li> <li>.value[2].i32: font style. This is an optional parameter. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Multiple fonts are separated by comma (,).</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE

```c
NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE
```

**Description**

Defines the size of the letter area of the alphabet index bar. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: diameter of the circle when the letter area is circular, in vp. The default value is <b>24</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: diameter of the circle when the letter area is circular, in vp.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_SELECTED

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED
```

**Description**

Defines the index of the selected item. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index of the selected item. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: index of the selected item.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_AUTO_COLLAPSE

```c
NODE_ARC_ALPHABET_AUTO_COLLAPSE
```

**Description**

Defines whether to collapse the characters when the space of the index bar is insufficient to display all characters. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to collapse the characters when the space of the index bar is insufficient to display all characters. The value <b>1</b> indicates to collapse the characters, and <b>0</b> indicates the opposite. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the characters are collapsed when the space of the index bar is insufficient to display all characters.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE

```c
NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE
```

**Description**

Defines the background blur style of the popup. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: background blur style of the popup. The parameter type is [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle). The default value is <b>ARKUI_BLUR_STYLE_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: background blur style of the popup.</li> </ul>

**Since**: 26.0.1

### NODE_SWIPER_LOOP

```c
NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER
```

**Description**

Defines whether to enable loop playback for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable loop playback. The value <b>1</b> means to enable loop playback, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable loop playback. The value <b>1</b> means to enable loop playback, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_AUTO_PLAY

```c
NODE_SWIPER_AUTO_PLAY
```

**Description**

Defines whether to enable automatic playback for child component switching in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b> means to enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> <li>.value[1]?.i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> means to stop automatic playback, and <b>0</b> means the opposite. The default value is <b>1</b>. This parameter is supported since API version 16.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether automatic playback is enabled for child component switching. The value <b>1</b> indicates automatic playback is enabled for child component switching, and <b>0</b> indicates the opposite. </li> <li>.value[1].i32: whether automatic playback is stopped when the user touches the screen. The value <b>1</b> means that automatic playback is stopped, and <b>0</b> means the opposite. This parameter is supported since API version 16.</li> </ul>

**Since**: 12

### NODE_SWIPER_SHOW_INDICATOR

```c
NODE_SWIPER_SHOW_INDICATOR
```

**Description**

Defines whether to show the navigation indicator for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show the navigation indicator. The value <b>1</b> means to show the navigation indicator, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the navigation indicator is shown. The value <b>1</b> indicates the navigation indicator is shown, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 12

### NODE_SWIPER_INTERVAL

```c
NODE_SWIPER_INTERVAL
```

**Description**

Defines the interval for automatic playback in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. **NODE_SWIPER_AUTO_PLAY** must be set to <b>1</b> (enable auto-play) first for the time interval set by this attribute to take effect.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: interval for automatic playback, in milliseconds. The value range is [0, +∞). The default value is <b>3000</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: interval for automatic playback, in ms.</li> </ul>

**Since**: 12

### NODE_SWIPER_VERTICAL

```c
NODE_SWIPER_VERTICAL
```

**Description**

Defines whether to use vertical swiping for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to use vertical swiping. The value <b>1</b> means to use vertical swiping, and <b>0</b> means to use horizontal swiping. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether vertical swiping is used. The value <b>1</b> indicates vertical sliding is used, and <b>0</b> indicates horizontal sliding is used.</li> </ul>

**Since**: 12

### NODE_SWIPER_DURATION

```c
NODE_SWIPER_DURATION
```

**Description**

Defines the duration of the animation for switching child components in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: duration of the animation for switching child components, in milliseconds. The value range is [0, +∞). The default value is <b>400</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: duration of the animation for switching child components, in milliseconds.</li> </ul>

**Since**: 12

### NODE_SWIPER_CURVE

```c
NODE_SWIPER_CURVE
```

**Description**

Defines the animation curve for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. If this attribute is not set or reset, the animation curve is curvesInterpolatingSpring(-1, 1, 328, 34). If an exception occurs (such as mismatching parameter type or invalid parameter) when setting this attribute, the default value <b>ARKUI_CURVE_LINEAR</b> is used.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is <b>ARKUI_CURVE_LINEAR</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve).</li> </ul>

**Since**: 12

### NODE_SWIPER_ITEM_SPACE

```c
NODE_SWIPER_ITEM_SPACE
```

**Description**

Defines the spacing between child components in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: spacing between child components, in vp. The value range is [0, +∞), and the default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: spacing between child components, in vp.</li> </ul>

**Since**: 12

### NODE_SWIPER_INDEX

```c
NODE_SWIPER_INDEX
```

**Description**

Defines the index of the child component currently displayed in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index of the child component. The value range is [0, Number of child components – 1]. The default value is <b>0</b>.</li> <li>.value[1]?.i32: swipe animation mode. The parameter type is [ArkUI_SwiperAnimationMode](capi-swiper-h.md#arkui_swiperanimationmode). The default value is <b>ARKUI_SWIPER_ANIMATION_MODE_NONE</b>. It is effective only for this setting. This parameter is supported since API version 15.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: index of the child component.</li> </ul>

**Since**: 12

### NODE_SWIPER_DISPLAY_COUNT

```c
NODE_SWIPER_DISPLAY_COUNT
```

**Description**

Defines the number of elements to display per page for the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of elements to display per page. The value range is [1, +∞). The default value is <b>1</b>.</li> <li>.value[1]?.i32: whether to paginate by group. The value <b>0</b> means to paginate by elements, and <b>1</b> means to paginate by groups of elements displayed within the viewport. The default value is <b>0</b>. This parameter is supported since API version 19.</li> <li>.string?: whether to enable auto-adaptation. This parameter accepts only the value <b>"auto"</b>. When this parameter is set to <b>"auto"</b>, the **value[]** parameters are ignored. If this parameter is not set, the **value[]** parameter is used. This parameter is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of elements to display per page.</li> <li>.value[1].i32: whether pagination by group is enabled. The value <b>0</b> indicates that pagination is performed by elements, and <b>1</b> indicates that pagination is performed by groups of elements displayed within the viewport. This parameter is supported since API version 19.</li> <li>.string: the value <b>auto</b> indicates the number of elements to display after being automatically adjusted. This parameter is supported since API version 19.</li> </ul>

**Since**: 12

### NODE_SWIPER_DISABLE_SWIPE

```c
NODE_SWIPER_DISABLE_SWIPE
```

**Description**

Defines whether to disable the swipe-to-switch feature of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. For example, you can disable the swipe-to-switch feature to allow page switching only through navigation arrows or indicators, or to prevent gesture sliding interference.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to disable the swipe-to-switch feature. The value <b>1</b> means to disable the feature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the swipe-to-switch feature is disabled. The value <b>1</b> indicates the swipe-to-switch feature is disabled, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 12

### NODE_SWIPER_SHOW_DISPLAY_ARROW

```c
NODE_SWIPER_SHOW_DISPLAY_ARROW
```

**Description**

Defines whether to show the arrow when the mouse pointer hovers over the navigation indicator in the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow). The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li> <li>?.object: style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). If this parameter is not set, the default arrow style is used. This parameter is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the arrow is shown when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow).</li> <li>.object: style of the arrow displayed when the mouse pointer hovers over the navigation indicator. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.</li> </ul>

**Since**: 12

### NODE_SWIPER_EDGE_EFFECT_MODE

```c
NODE_SWIPER_EDGE_EFFECT_MODE
```

**Description**

Defines the effect used at the edges of the **Swiper** component when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs. When the **Swiper** component has reached the first or last child component, the edge effect is triggered if the user continues to slide.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is <b>ARKUI_EDGE_EFFECT_SPRING</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: effect used at the edges of the component when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).</li> </ul>

**Since**: 12

### NODE_SWIPER_NODE_ADAPTER

```c
NODE_SWIPER_NODE_ADAPTER
```

**Description**

Defines the adapter of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. The adapter is used when the **Swiper** component needs to dynamically load or reuse child components, for example, list carousel with a large amount of data and carousel with an infinite loop.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: ArkUI_NodeAdapter object used as the adapter. You are advised to use this parameter together with **NODE_SWIPER_CACHED_COUNT** to improve performance.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: adapter object. The parameter type is ArkUI_NodeAdapter, used to dynamically load or reuse **Swiper** child components.</li> </ul>

**Since**: 12

### NODE_SWIPER_CACHED_COUNT

```c
NODE_SWIPER_CACHED_COUNT
```

**Description**

Defines the number of cached items in the adapter of the **Swiper** component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used to optimize the **Swiper** performance. When the rendering of child components is complex or more pages need to be preloaded, you can increase the number of cached items.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of cached items in the adapter of **Swiper**. The value range is [0, +∞). The default value is <b>1</b>. You are advised to set this parameter based on the actual service scenario to avoid high memory usage.</li> <li>.value[1]?.i32: whether to show cached items. The value <b>0</b> means to hide cached items, and <b>1</b> means to show cached items. The default value is <b>0</b>. This parameter is supported since API version 19.</li> <li>.value[2]?.i32: whether the number of cached items is calculated by group. The value <b>0</b> indicates that the number of cached items is calculated by group when **NODE_SWIPER_DISPLAY_COUNT** is set to pagination by group. The value <b>1</b> indicates that the actual number of cached items is used. The default value is <b>0</b>. This parameter is supported since API version 24.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of cached items in the adapter of **Swiper**.</li> <li>.value[1].i32: whether cached items are shown. The value <b>0</b> means cached items are hidden, and <b>1</b> means cached items are shown. This parameter is supported since API version 19.</li> <li>.value[2].i32: whether the number of cached items is calculated by group. The value <b>0</b> means the number of cached items is calculated by group, and <b>1</b> means the actual number of cached items is used. This parameter is supported since API version 24.</li> </ul>

**Since**: 12

### NODE_SWIPER_PREV_MARGIN

```c
NODE_SWIPER_PREV_MARGIN
```

**Description**

Defines the leading margin of the **Swiper** component. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: leading margin, in vp. The value range is [0, +∞). The default value is <b>0</b>.</li> <li>.value[1]?.i32: whether to ignore blank areas. The value <b>1</b> indicates to ignore blank areas, and <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: leading margin, in vp.</li> <li>.value[1].i32: whether blank areas are ignored. The value <b>1</b> indicates blank areas are ignored, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 12

### NODE_SWIPER_NEXT_MARGIN

```c
NODE_SWIPER_NEXT_MARGIN
```

**Description**

Defines the trailing margin of the **Swiper** component. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: trailing margin, in vp. The value range is [0, +∞). The default value is <b>0</b>.</li> <li>.value[1]?.i32: whether to ignore blank areas. The value <b>1</b> indicates to ignore blank areas, and <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: trailing margin, in vp.</li> <li>.value[1].i32: whether blank areas are ignored. The value <b>1</b> indicates blank areas are ignored, and <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_INDICATOR

```c
NODE_SWIPER_INDICATOR
```

**Description**

Defines the navigation indicator type of the **Swiper** component. The attribute can be set, reset, and obtained as required through APIs. <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b> is applicable to scenarios such as carousel images and ad slots. <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b> is applicable to scenarios where the current page number needs to be displayed, such as readers and galleries.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype). The default value is <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>.</li> <li>.object: additional configuration for the navigation indicator, depending on the type. For <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>, the parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md). For <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>, the parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md). [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: navigation indicator type. The parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype).</li> <li>.object: additional configuration for the navigation indicator, depending on the type. For <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>, the parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md). For <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>, the parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md). [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19.</li> </ul>

**Since**: 12

### NODE_SWIPER_NESTED_SCROLL

```c
NODE_SWIPER_NESTED_SCROLL
```

**Description**

Defines the nested scrolling mode of the **Swiper** component and its parent component. This attribute can be set, reset, and obtained as required through APIs. This attribute is used when **Swiper** is nested in scrollable containers such as **ScrollView** and **List**, to coordinate scrolling behavior and avoid scrolling conflicts.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: nested scrolling mode of the **Swiper** component and its parent component. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode). It takes effect only when the **Swiper** component is nested in a scrollable container. The default value is <b>ARKUI_SWIPER_NESTED_SCROLL_SELF_ONLY</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: nested scrolling mode. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode).</li> </ul>

**Since**: 12

### NODE_SWIPER_SWIPE_TO_INDEX

```c
NODE_SWIPER_SWIPE_TO_INDEX
```

**Description**

Sets the **Swiper** component to switch to the specified page. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows. This attribute cannot be reset or obtained through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index of the target page in the Swiper component. The value range is [0, Number of pages – 1].</li> <li>.value[1]?.i32: whether to use an animation when the target page is reached. The value <b>1</b> indicates to use the animation, and <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_INDICATOR_INTERACTIVE

```c
NODE_SWIPER_INDICATOR_INTERACTIVE
```

**Description**

Defines whether the navigation indicator of a component is interactive.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the navigation indicator of a component is interactive. The value <b>1</b> indicates that the navigation indicator is interactive, and <b>0</b> indicates the opposite. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the navigation indicator of a component is interactive. The value <b>1</b> indicates that the navigation indicator is interactive, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 12

### NODE_SWIPER_PAGE_FLIP_MODE

```c
NODE_SWIPER_PAGE_FLIP_MODE
```

**Description**

Defines the page flipping mode using the mouse wheel. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode). The default value is <b>ARKUI_PAGE_FLIP_MODE_CONTINUOUS</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode).</li> </ul>

**Since**: 15

### NODE_SWIPER_AUTO_FILL

```c
NODE_SWIPER_AUTO_FILL
```

**Description**

Configures the **Swiper** component to automatically adjust the number of elements displayed per page based on the minimum width of the elements. This attribute can be set, reset, and obtained as required through APIs. This attribute is applicable to responsive layout. It is used when the number of elements displayed per page needs to be automatically adjusted based on the container width, such as in landscape mode or multi-device adaptation scenarios.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum width of the elements, in vp. The value range is (0, +∞).</li> <li>.value[1]?.i32: whether to paginate by group. The value <b>0</b> means to paginate by elements, and <b>1</b> means to paginate by groups of elements displayed within the viewport. The default value is <b>0</b>. </li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum width of the elements, in vp.</li> <li>.value[1].i32: whether pagination by group is enabled. The value <b>0</b> indicates that pagination is performed by elements, and <b>1</b> indicates that pagination is performed by groups of elements displayed within the viewport.</li> </ul>

**Since**: 19

### NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION

```c
NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023
```

**Description**

Defines whether to maintain the visible content's position when a child component is inserted or deleted outside the display area of the **Swiper** component. This attribute can be used to maintain the content currently displayed when a child component is dynamically added or deleted in **Swiper**, for example, in the chat record list and offering list.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to maintain the visible content's position when a child component is inserted or deleted outside the display area of the **Swiper** component. The value <b>1</b> indicates to maintain the visible content's position, and <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the visible content's position is maintained when a child component is inserted or deleted outside the display area of the **Swiper** component. The value <b>1</b> indicates that the visible content's position is maintained, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 20

### NODE_SWIPER_ITEMFILLPOLICY

```c
NODE_SWIPER_ITEMFILLPOLICY = 1001024
```

**Description**

Defines the responsive layout policy of the **Swiper** component, used to automatically adjust the number of child component columns displayed on a page based on different breakpoint specifications. This attribute can be set, reset, and obtained as required through APIs. This attribute is used to adaptively adjust the number of columns displayed on each page based on different screen sizes, such as in landscape mode or multi-device adaptation scenarios.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The parameter type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> <li>.value[1]?.i32: whether to paginate by group. The value <b>0</b> means to paginate by elements, and <b>1</b> means to paginate by groups of elements displayed within the viewport. The default value is <b>0</b>. </li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: responsive layout policy. The parameter type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> <li>.value[1].i32: whether pagination by group is enabled. The value <b>0</b> indicates that pagination is performed by elements, and <b>1</b> indicates that pagination is performed by groups of elements displayed within the viewport.</li> </ul>

**Since**: 22

### NODE_ARC_SWIPER_INDEX

```c
NODE_ARC_SWIPER_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SWIPER
```

**Description**

Defines the index of the child component currently displayed in the ArcSwiper. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index value of the child component. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: index value of the child component.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_INDICATOR

```c
NODE_ARC_SWIPER_INDICATOR
```

**Description**

Defines the navigation dot indicator of the **ArcSwiper** component. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to display the navigation dot indicator. The value <b>1</b> indicates to display, and <b>0</b> indicates the opposite. The default value is <b>1</b>.</li> <li>.value[1].i32: direction of the **ArcSwiper** navigation dot indicator. The parameter type is [OH_ArkUI_ArcDirection](capi-native-type-h.md#oh_arkui_arcdirection). The default value is <b>OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION</b>. This is an optional parameter.</li> <li>.value[2].i32: color of the unselected dot, in 0xARGB format. The default value is <b>0xA9FFFFFF</b>, which indicates white. This is an optional parameter.</li> <li>.value[3].i32: color of the selected dot, in 0xARGB format. The default value is <b>0xFF5EA1FF</b>, which indicates blue. This is an optional parameter.</li> <li>.value[4].i32: background color of the **ArcSwiper** navigation dot indicator after a long press, in 0xARGB format. The default value is <b>0xFF5EA1FF</b>, which indicates blue. This is an optional parameter. </li> <li>.object: gradient color of the mask. This is an optional parameter. In a color stop array, each color stop consists of a color and its stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. <b>colors</b>: color of the color stop. <b>stops</b>: stop of the color. <b>size</b>: number of colors.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the navigation dot indicator is displayed.</li> <li>.value[1].i32: direction of the **ArcSwiper** navigation dot indicator.</li> <li>.value[2].u32: color of the unselected dot.</li> <li>.value[3].u32: color of the selected dot.</li> <li>.value[4].u32: background color of the **ArcSwiper** navigation dot indicator after a long press.</li> <li>.object: gradient color of the mask.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DURATION

```c
NODE_ARC_SWIPER_DURATION
```

**Description**

Defines the animation duration for child component switching. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: animation duration for child component switching, in milliseconds. The value range is [0, +∞). When not set, the default value is <b>400</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: animation duration for child component switching, in milliseconds.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_VERTICAL

```c
NODE_ARC_SWIPER_VERTICAL
```

**Description**

Defines whether to use vertical swiping. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to use vertical swiping. The value <b>1</b> indicates to use vertical swiping, and <b>0</b> indicates to use horizontal swiping. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether vertical swiping is used.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DISABLE_SWIPE

```c
NODE_ARC_SWIPER_DISABLE_SWIPE
```

**Description**

Whether to disable swiping. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disable the swipe feature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to disable the swipe feature.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY

```c
NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY
```

**Description**

Sensitivity of rotating the digital crown. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the sensitivity of rotating crown. The parameter type is [ArkUI_CrownSensitivity](capi-native-type-h.md#arkui_crownsensitivity). The default value is <b>ARKUI_CROWN_SENSITIVITY_MEDIUM</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the sensitivity of rotating crown.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_EFFECT_MODE

```c
NODE_ARC_SWIPER_EFFECT_MODE
```

**Description**

Edge swipe effect of the **ArcSwiper** component when swiping to the boundary of the scrollable content. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is <b>ARKUI_EDGE_EFFECT_SPRING</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION

```c
NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION
```

**Description**

Whether to disable the transition animation. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to disable the transition animation. The value <b>1</b> means to disable the transition animation, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to disable the transition animation.</li> </ul>

**Since**: 26.0.1


