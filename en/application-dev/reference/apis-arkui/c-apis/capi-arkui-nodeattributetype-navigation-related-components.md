# Navigation Related Components

## Overview

Defines the ArkUI style attributes that can be set on the native side.

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

Defines the index item text color in normal state. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the text, in 0xARGB format, and the default value is 0x99182431.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the text, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR
```

**Description**

Defines the index item text color in selected state. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the text, in 0xARGB format, and the default value is 0xFF007DFF.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the text, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR
```

**Description**

Defines the pop-up window text color. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the text, in 0xARGB format, and the default value is 0xFF007DFF.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the text, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR
```

**Description**

Defines the index item background color in selected state. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the background, in 0xARGB format, and the default value is 0xFF1F71FF.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the background, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR
```

**Description**

Defines the pop-up window background color. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the background, in 0xARGB format, and the default value is 0xD8404040.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the background, in 0xARGB format.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_USE_POPUP

```c
NODE_ARC_ALPHABET_INDEXER_USE_POPUP
```

**Description**

Defines whether to use a pop-up window. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to use a pop-up. The value <b>0</b> means not to use a pop-up, and <b>1</b> means to use a pop-up. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to use a pop-up.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_SELECTED_FONT

```c
NODE_ARC_ALPHABET_SELECTED_FONT
```

**Description**

Defines the font style of the selected index. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts. Optional. The default value is <b>"HarmonyOS Sans"</b>.</li> <li>.value[0].f32: font size, in fp. Optional. The default value is <b>13</b>.</li> <li>.value[1].i32: font weight. Optional. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_W500</b>.</li> <li>.value[2].i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_POPUP_FONT

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_FONT
```

**Description**

Defines the font style of the pop-up window. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts. Optional. The default value is <b>"HarmonyOS Sans"</b>.</li> <li>.value[0].f32: font size, in fp. Optional. The default value is <b>19</b>.</li> <li>.value[1].i32: font weight. Optional. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_W500</b>.</li> <li>.value[2].i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_FONT

```c
NODE_ARC_ALPHABET_FONT
```

**Description**

Defines the default font style. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts. Optional. The default value is <b>"HarmonyOS Sans"</b>.</li> <li>.value[0].f32: font size, in fp. Optional. The default value is <b>13</b>.</li> <li>.value[1].i32: font weight. Optional. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_W500</b>.</li> <li>.value[2].i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE

```c
NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE
```

**Description**

Defines the letter index bar letter area size. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: the letter area is a circle, set the diameter of the circle, in vp. The default value is <b>24</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: the letter area is a circle, set the diameter of the circle, in vp.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_INDEXER_SELECTED

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED
```

**Description**

Defines the selected index. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the selected index. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the selected index.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_AUTO_COLLAPSE

```c
NODE_ARC_ALPHABET_AUTO_COLLAPSE
```

**Description**

Defines whether to collapse the characters when the indexer bar is not enough to display all characters. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to collapse the characters when the indexer bar is not enough to display all characters.The value <b>1</b> means to automatically collapses the characters, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to collapse the characters when the indexer bar is not enough to display all characters.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE

```c
NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE
```

**Description**

Defines the background blur style of the pop-up window. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: blur style of the pop-up window. The value is an enum of [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle). The default value is <b>ARKUI_BLUR_STYLE_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: blur style of the pop-up window.</li> </ul>

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

Defines whether to enable automatic playback for child component switching in the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b> means to enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> <li>.value[1]?.i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> means to stop automatic playback, and <b>0</b> means the opposite. The default value is <b>1</b>. This parameter is supported since API version 16.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable automatic playback for child component switching. The value <b>1</b> means to enable automatic playback, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> <li>.value[1].i32: whether to stop automatic playback when the user touches the screen. The value <b>1</b> means to stop automatic playback, and <b>0</b> means the opposite. This parameter is supported since API version 16. </li> </ul>

**Since**: 12

### NODE_SWIPER_SHOW_INDICATOR

```c
NODE_SWIPER_SHOW_INDICATOR
```

**Description**

Defines whether to enable the navigation point indicator for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the navigation point indicator. The value <b>1</b> means to enable the navigation point indicator, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable the navigation point indicator. The value <b>1</b> means to enable the navigation point indicator, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_INTERVAL

```c
NODE_SWIPER_INTERVAL
```

**Description**

Defines the interval for automatic playback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: interval for automatic playback, in milliseconds.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: interval for automatic playback, in milliseconds.</li> </ul>

**Since**: 12

### NODE_SWIPER_VERTICAL

```c
NODE_SWIPER_VERTICAL
```

**Description**

Defines whether vertical swiping is used for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether vertical swiping is used. The value <b>1</b> means that vertical swiping is used, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether vertical swiping is used. The value <b>1</b> means that vertical swiping is used, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_DURATION

```c
NODE_SWIPER_DURATION
```

**Description**

Defines the duration of the animation for switching child components. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: duration of the animation for switching child components, in milliseconds. The default value is <b>400</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: duration of the animation for switching child components, in milliseconds. The default value is <b>400</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_CURVE

```c
NODE_SWIPER_CURVE
```

**Description**

Defines the animation curve for the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is <b>ARKUI_CURVE_LINEAR</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: animation curve. The parameter type is [ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve). The default value is <b>ARKUI_CURVE_LINEAR</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_ITEM_SPACE

```c
NODE_SWIPER_ITEM_SPACE
```

**Description**

Defines the spacing between child components in the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: spacing between child components.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: spacing between child components.</li> </ul>

**Since**: 12

### NODE_SWIPER_INDEX

```c
NODE_SWIPER_INDEX
```

**Description**

Defines the index of the child component currently displayed in the swiper. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: index value of the child component.</li> <li>.value[1]?.i32: animation mode, the parameter type is [ArkUI_SwiperAnimationMode](capi-swiper-h.md#arkui_swiperanimationmode). The default value is ARKUI_SWIPER_NO_ANIMATION. This parameter is valid only for the current call. This parameter is supported since API version 15.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: index value of the child component.</li> </ul>

**Since**: 12

### NODE_SWIPER_DISPLAY_COUNT

```c
NODE_SWIPER_DISPLAY_COUNT
```

**Description**

Defines the number of elements to display per page. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of elements to display per page.</li> <li>.value[1]?.i32: whether to turn pages by group. The value <b>0</b> means to turn pages by child element, and <b>1</b> means to turn pages by group. This parameter is supported since API version 19.</li> <li>.string?: this parameter can only be set to 'auto'. When 'auto' is set, the value[] parameters are ignored. This parameter is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of elements to display per page.</li> <li>.value[1].i32: whether to turn pages by group. This parameter is supported since API version 19.</li> <li>.string: 'auto' or empty string.</li> </ul>

**Since**: 12

### NODE_SWIPER_DISABLE_SWIPE

```c
NODE_SWIPER_DISABLE_SWIPE
```

**Description**

Defines whether to disable the swipe feature. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disable the swipe feature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disable the swipe feature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul>

**Since**: 12

### NODE_SWIPER_SHOW_DISPLAY_ARROW

```c
NODE_SWIPER_SHOW_DISPLAY_ARROW
```

**Description**

Defines whether to show the arrow when the mouse pointer hovers over the navigation point indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow). The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li> <li>.?object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to show the arrow when the mouse pointer hovers over the navigation point indicator. The parameter type is [ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow). The default value is <b>ARKUI_SWIPER_ARROW_HIDE</b>.</li> <li>.object: arrow style. The parameter type is [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md). This parameter is supported since API version 19.</li> </ul>

**Since**: 12

### NODE_SWIPER_EDGE_EFFECT_MODE

```c
NODE_SWIPER_EDGE_EFFECT_MODE
```

**Description**

Defines the effect used at the edges of the swiper when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is <b>ARKUI_EDGE_EFFECT_SPRING</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).</li> </ul>

**Since**: 12

### NODE_SWIPER_NODE_ADAPTER

```c
NODE_SWIPER_NODE_ADAPTER
```

**Description**

Defines the swiper adapter. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: {@link ArkUI_NodeAdapter} object as the adapter.</li> </ul>

**Since**: 12

### NODE_SWIPER_CACHED_COUNT

```c
NODE_SWIPER_CACHED_COUNT
```

**Description**

Sets the number of cached items in the swiper adapter. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of cached items in the swiper adapter.</li> <li>.value[1]?.i32: whether the cached items will be displayed. The value <b>0</b> indicates that cached items will not be displayed, and <b>1</b> indicates that cached items will be displayed. The default value is <b>0</b>. This parameter is supported from API version 19.</li> <li>.value[2]?.i32: whether the cachedCount is independent of group calculation. The value <b>1</b> indicates that cachedCount is calculated by actual child component count, and is independent of displayCount group calculation. The value <b>0</b> indicates that, when NODE_SWIPER_DISPLAY_COUNT is enabled to turn pages by group, cachedCount is calculated by group.The default value is <b>0</b>. This parameter is supported from API version 24.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of cached items in the swiper adapter.</li> <li>.value[1].i32: whether the cached items will be displayed. This parameter is supported from API version 19. </li> <li>.value[2].i32: whether the cachedCount is independent of group calculation. This parameter is supported from API version 24.</li> </ul>

**Since**: 12

### NODE_SWIPER_PREV_MARGIN

```c
NODE_SWIPER_PREV_MARGIN
```

**Description**

Defines the front margin of the wiper. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: the front margin. The unit is vp. The default value is <b>0.0</b></li> <li>.value[1]?.i32: whether to ignore blanks, the default value is 0. The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: the front margin, the unit is vp.</li> <li>.value[1].i32: whether to ignore blank areas. The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_SWIPER_NEXT_MARGIN

```c
NODE_SWIPER_NEXT_MARGIN
```

**Description**

Defines the back margin of the wiper. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: the back margin. The unit is vp. The default value is <b>0.0</b></li> <li>.value[1]?.i32: whether to ignore blanks, the default value is 0. The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: the back margin, the unit is vp.</li> <li>.value[1].i32: whether to ignore blank areas. The value <b>1</b> means to ignore blank areas, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_SWIPER_INDICATOR

```c
NODE_SWIPER_INDICATOR
```

**Description**

Defines the navigation indicator type of the swiper. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: navigation indicator type, the parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype).</li> <li>.object: The parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>. The parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>. [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: navigation indicator type, the parameter type is [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype).</li> <li>.object: The parameter type is [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DOT</b>. The parameter type is [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) when the indicator type is <b>ARKUI_SWIPER_INDICATOR_TYPE_DIGIT</b>. [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) is supported since API version 19.</li> </ul>

**Since**: 12

### NODE_SWIPER_NESTED_SCROLL

```c
NODE_SWIPER_NESTED_SCROLL
```

**Description**

Set the nested scrolling mode for the Swiper component and parent component.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32：Nested scrolling patterns for Swiper components and parent components. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode) The default value is <b>ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY</b></li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32：Nested scrolling patterns for Swiper components and parent components. The parameter type is [ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode)</li> </ul>

**Since**: 12

### NODE_SWIPER_SWIPE_TO_INDEX

```c
NODE_SWIPER_SWIPE_TO_INDEX
```

**Description**

Set the switcher component to flip to the specified page.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32：Specify the index value of the page in Swiper.</li> <li>.value[1]?.i32：Set whether there is an animation effect when flipping to the specified page. 1 indicates active effect, 0 indicates no active effect, default value is 0。</li> </ul>

**Since**: 12

### NODE_SWIPER_INDICATOR_INTERACTIVE

```c
NODE_SWIPER_INDICATOR_INTERACTIVE
```

**Description**

Set to disable component navigation point interaction function。<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32：Set to disable the interaction function of component navigation points. When set to true, it indicates that the navigation points are interactive. The default value is true.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32：Set to disable component navigation point interaction.</li> </ul>

**Since**: 12

### NODE_SWIPER_PAGE_FLIP_MODE

```c
NODE_SWIPER_PAGE_FLIP_MODE
```

**Description**

Sets the page flipping mode using the mouse wheel.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: page flipping mode using the mouse wheel. The parameter type is [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode). </li> </ul><br> **Format of the return value [ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode):**<br><ul> <li>.value[0].i32: page flipping mode using the mouse wheel.</li> </ul>

**Since**: 15

### NODE_SWIPER_AUTO_FILL

```c
NODE_SWIPER_AUTO_FILL
```

**Description**

Defines the minimum main axis size of child element for swiper to works out the display count. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum main axis size of the child element, Unit: vp.</li> <li>.value[1]?.i32: whether to turn pages by group. The value <b>0</b> means to turn pages by child element, and <b>1</b> means to turn pages by group. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum main axis size of the child element, Unit: vp.</li> <li>.value[1].i32: whether to turn pages by group.</li> </ul>

**Since**: 19

### NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION

```c
NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023
```

**Description**

Sets whether to maintain the visible content's position when data is inserted or deleted outside the display area of the <b>Swiper</b> component.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the <b>Swiper</b> component. The value <b>0</b> means not to maintain the visible content's position, and <b>1</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to maintain the visible content's position when data is inserted or deleted outside the display area of the <b>Swiper</b> component. The value <b>0</b> means not to maintain the visible content's position, and <b>1</b> means the opposite. The default value is <b>0</b>.</li> </ul>

**Since**: 20

### NODE_SWIPER_ITEMFILLPOLICY

```c
NODE_SWIPER_ITEMFILLPOLICY = 1001024
```

**Description**

Specifies the responsive column layout policy for the <b>Swiper</b> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> <li>.value[1]?.i32: whether to paginate by group. The value <b>0</b> means to paginate by individual child elements, and <b>1</b> means to paginate by groups of child elements displayed within the viewport. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of columns at different breakpoint specifications. The data type is [ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy).</li> <li>.value[1].i32: whether to paginate by group.</li> </ul>

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

Defines the indicator type of the ArcSwiper. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show indicator. The value <b>1</b> means to show indicator, and <b>0</b> means the opposite. The default value is <b>1</b>.</li> <li>.value[1].i32: direction of the ArcSwiper indicator. The parameter type is [OH_ArkUI_ArcDirection](capi-native-type-h.md#oh_arkui_arcdirection). The default value is <b>OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION</b>. Optional.</li> <li>.value[2].u32: color of the unselected points, in 0xARGB format, and the default value is <b>0xA9FFFFFF</b>. Optional.</li> <li>.value[3].u32: color of the selected point, in 0xARGB format, and the default value is <b>0xFF5EA1FF</b>. Optional.</li> <li>.value[4].u32: background color of the ArcSwiper indicator after long pressed, in 0xARGB format, and the default value is <b>0xFF5EA1FF</b>. Optional.</li> <li>.object: gradient color for the mask. Optional. Array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to show indicator.</li> <li>.value[1].i32: direction of the ArcSwiper indicator.</li> <li>.value[2].u32: color of the unselected points.</li> <li>.value[3].u32: color of the selected point.</li> <li>.value[4].u32: background color of the ArcSwiper indicator after long pressed.</li> <li>.object: gradient color for the mask.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DURATION

```c
NODE_ARC_SWIPER_DURATION
```

**Description**

Defines the animation duration. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: the animation duration, in ms. The default value is <b>400</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: the animation duration.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_VERTICAL

```c
NODE_ARC_SWIPER_VERTICAL
```

**Description**

Defines whether to display vertically. The attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to display vertically. The value <b>1</b> means to display vertically, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to display vertically.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DISABLE_SWIPE

```c
NODE_ARC_SWIPER_DISABLE_SWIPE
```

**Description**

Defines whether to disable the swipe feature. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to disable the swipe feature. The value <b>1</b> means to disable the swipe feature, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to disable the swipe feature.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY

```c
NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY
```

**Description**

Defines the sensitivity of rotating crown. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: the sensitivity of rotating crown. The parameter type is {@link ArkUI_CrownSensitivity}.<br>The default value is <b>ARKUI_CROWN_SENSITIVITY_MEDIUM</b>.</li><br></ul><br>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul><br><li>.value[0].i32: the sensitivity of rotating crown.</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_EFFECT_MODE

```c
NODE_ARC_SWIPER_EFFECT_MODE
```

**Description**

Defines the effect used at the edges of the ArcSwiper when the boundary of the scrollable content is reached. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect). The default value is <b>ARKUI_EDGE_EFFECT_SPRING</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: effect used at the edges of the swiper when the boundary of the scrollable content is reached. The parameter type is [ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect).</li> </ul>

**Since**: 26.0.1

### NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION

```c
NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION
```

**Description**

Defines whether to disable the transition animation. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to disable the transition animation. The value <b>1</b> means to disable the transition animation, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to disable the transition animation.</li> </ul>

**Since**: 26.0.1


