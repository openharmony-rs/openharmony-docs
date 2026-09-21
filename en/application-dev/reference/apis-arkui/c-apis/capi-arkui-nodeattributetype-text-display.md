# Text Display

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_CONTENT

```c
NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT
```

**Description**

Defines the text content attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: text content.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: text content.</li> </ul>

**Since**: 12

### NODE_FONT_COLOR

```c
NODE_FONT_COLOR
```

**Description**

Defines the font color attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: font color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: font color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_FONT_SIZE

```c
NODE_FONT_SIZE
```

**Description**

Defines the font size attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: font size, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: font size, in fp.</li> </ul>

**Since**: 12

### NODE_FONT_STYLE

```c
NODE_FONT_STYLE
```

**Description**

Defines the font style attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font style [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font style [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 12

### NODE_FONT_WEIGHT

```c
NODE_FONT_WEIGHT
```

**Description**

Defines the font weight attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul>

**Since**: 12

### NODE_TEXT_LINE_HEIGHT

```c
NODE_TEXT_LINE_HEIGHT
```

**Description**

Defines the text line height attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: line height, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: line height, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_DECORATION

```c
NODE_TEXT_DECORATION
```

**Description**

Defines the text decoration style and color. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype). The default value is <b>ARKUI_TEXT_DECORATION_TYPE_NONE</b>.</li> <li>.value[1]?.u32: text decoration color, in 0xARGB format. For example, 0xFFFF0000 indicates red. Optional.</li> <li>.value[2]?.i32: text decoration style [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle).</li> <li>.value[3]?.f32: text decoration thickness scale. This parameter is supported since API version 22.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text decoration type [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype).</li> <li>.value[1].u32: text decoration color, in 0xARGB format.</li> <li>.value[2].i32: text decoration style [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle).</li> <li>.value[3]?.f32: text decoration thickness scale. This parameter is supported since API version 22.</li> </ul>

**Since**: 12

### NODE_TEXT_CASE

```c
NODE_TEXT_CASE
```

**Description**

Defines the text case attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text case.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text case.</li> </ul>

**Since**: 12

### NODE_TEXT_LETTER_SPACING

```c
NODE_TEXT_LETTER_SPACING
```

**Description**

Defines the letter spacing attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: letter spacing, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: letter spacing, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_MAX_LINES

```c
NODE_TEXT_MAX_LINES
```

**Description**

Sets the maximum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: maximum number of lines in the text.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: maximum number of lines in the text.</li> </ul>

**Since**: 12

### NODE_TEXT_ALIGN

```c
NODE_TEXT_ALIGN
```

**Description**

Horizontal alignment mode of the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: horizontal alignment mode of the text. The value is an enum of [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: horizontal alignment mode of the text. The value is an enum of [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment).</li> </ul>

**Since**: 12

### NODE_TEXT_OVERFLOW

```c
NODE_TEXT_OVERFLOW
```

**Description**

Defines the text overflow attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: display mode when the text is too long. [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: display mode when the text is too long. [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).</li> </ul>

**Since**: 12

### NODE_FONT_FAMILY

```c
NODE_FONT_FAMILY
```

**Description**

Defines the font family attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: fonts, separated by commas (,).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: fonts, separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_COPY_OPTION

```c
NODE_TEXT_COPY_OPTION
```

**Description**

Defines the copy option attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: copy option [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is <b>ARKUI_COPY_OPTIONS_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: copy option [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions).</li> </ul>

**Since**: 12

### NODE_TEXT_BASELINE_OFFSET

```c
NODE_TEXT_BASELINE_OFFSET
```

**Description**

Defines the text baseline offset attribute This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_TEXT_SHADOW

```c
NODE_TEXT_TEXT_SHADOW
```

**Description**

Defines the text shadow attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: blur radius of the shadow, in vp.</li> <li>.value[1].i32: shadow type [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>.</li> <li>.value[2].u32: shadow color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <li>.value[3].f32: offset of the shadow along the x-axis, in vp.</li> <li>.value[4].f32: offset of the shadow along the y-axis, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: blur radius of the shadow, in vp.</li> <li>.value[1].i32: shadow type [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype).</li> <li>.value[2].u32: shadow color, in 0xARGB format.</li> <li>.value[3].f32: offset of the shadow along the x-axis, in vp.</li> <li>.value[4].f32: offset of the shadow along the y-axis, in vp.</li> </ul>

**Since**: 12

### NODE_TEXT_MIN_FONT_SIZE

```c
NODE_TEXT_MIN_FONT_SIZE
```

**Description**

Defines the minimum font size attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum font size, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum font size, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_MAX_FONT_SIZE

```c
NODE_TEXT_MAX_FONT_SIZE
```

**Description**

Defines the maximum font size attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum font size, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum font size, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_FONT

```c
NODE_TEXT_FONT
```

**Description**

Defines the text style attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string?: font family. Optional. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1]?.i32: font weight. Optional. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> <li>.value[2]?.i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_HEIGHT_ADAPTIVE_POLICY

```c
NODE_TEXT_HEIGHT_ADAPTIVE_POLICY
```

**Description**

Defines how the adaptive height is determined for the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: how the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-text-h.md#arkui_textheightadaptivepolicy).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: how the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-text-h.md#arkui_textheightadaptivepolicy).</li> </ul>

**Since**: 12

### NODE_TEXT_INDENT

```c
NODE_TEXT_INDENT
```

**Description**

Defines the indentation of the first line. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: indentation of the first line.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: indentation of the first line.</li> </ul>

**Since**: 12

### NODE_TEXT_WORD_BREAK

```c
NODE_TEXT_WORD_BREAK
```

**Description**

Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak).</li> </ul>

**Since**: 12

### NODE_TEXT_ELLIPSIS_MODE

```c
NODE_TEXT_ELLIPSIS_MODE
```

**Description**

Defines the ellipsis position. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode).</li> </ul>

**Since**: 12

### NODE_TEXT_LINE_SPACING

```c
NODE_TEXT_LINE_SPACING
```

**Description**

Defines the text line spacing attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: line spacing, in fp.</li> <li>?.object: Optional. Pointer to [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object for line spacing options. Available since API version 26.0.1. Use [OH_ArkUI_NativeModule_LineSpacingOptions_Create](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_create) to create and [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy the object.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: line spacing, in fp.</li> <li>.object: pointer to [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object for line spacing options. Available since API version 26.0.1.</li> </ul>

**Since**: 12

### NODE_FONT_FEATURE

```c
NODE_FONT_FEATURE
```

**Description**

Set the text feature effect and the NODE_FONT_FEATURE attribute, NODE_FONT_FEATURE is the advanced typesetting capability of OpenType Features such as ligatures and equal-width digits are generally used in customized fonts. The capabilities need to be supported by the fonts, Interfaces for setting, resetting, and obtaining attributes are supported. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: complies with the text feature format. The format is normal \| is in the format of [ \| on \| off]. There can be multiple values separated by commas (,). For example, the input format of a number with the same width is ss01 on.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string indicates the content of the text feature. Multiple text features are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_ENABLE_DATA_DETECTOR
```

**Description**

Setting Enable Text Recognition.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32:Enable text recognition, default value false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Enable Text Recognition.</li> </ul>

**Since**: 12

### NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG
```

**Description**

Set the text recognition configuration.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0...].i32: Array of entity types, parameter types [ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0...].i32: Array of entity types, parameter types [ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype).</li> </ul>

**Since**: 12

### NODE_TEXT_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_SELECTED_BACKGROUND_COLOR
```

**Description**

Defines the background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_CONTENT_WITH_STYLED_STRING

```c
NODE_TEXT_CONTENT_WITH_STYLED_STRING
```

**Description**

The text component uses a formatted string object to set text content properties, and supports property setting, property reset, and property acquisition interfaces.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object indicates ArkUI_StyledString formatted string data. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object indicates ArkUI_StyledString formatted string data. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).</li> </ul>

**Since**: 12

### NODE_TEXT_HALF_LEADING

```c
NODE_TEXT_HALF_LEADING = 1029
```

**Description**

Sets whether to center text vertically in the text component.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to center text vertically. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to center text vertically.</li> </ul>

**Since**: 12

### NODE_IMMUTABLE_FONT_WEIGHT

```c
NODE_IMMUTABLE_FONT_WEIGHT = 1030
```

**Description**

Defines the font weight attribute, which can be set, reset, and obtained as required through APIs. The font weight specified by this API is not affected by any changes in the system font weight settings.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul>

**Since**: 15

### NODE_TEXT_LINE_COUNT

```c
NODE_TEXT_LINE_COUNT = 1031
```

**Description**

Defines the text line count attribute, which can only be obtained as required through APIs.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: line count of the node.</li> </ul>

**Since**: 20

### NODE_TEXT_OPTIMIZE_TRAILING_SPACE

```c
NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032
```

**Description**

Sets whether to optimize the trailing spaces at the end of each line during text layout. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to optimize trailing spaces at the end of each line during text layout. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to optimize trailing spaces at the end of each line during text layout.</li> </ul>

**Since**: 20

### NODE_TEXT_LINEAR_GRADIENT

```c
NODE_TEXT_LINEAR_GRADIENT = 1033
```

**Description**

Sets a linear gradient effect for text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: start angle of the linear gradient. The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>.</li> <li>.value[1].i32: direction of the linear gradient. When a direction other than <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).</li> <li>.value[2].i32: whether the colors are repeated. The default value is <b>false</b>.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: start angle of the linear gradient. When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value; otherwise, it is at default value.</li> <li>.value[1].i32: direction of the linear gradient.</li> <li>.value[2].i32: whether the colors are repeated.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 20

### NODE_TEXT_RADIAL_GRADIENT

```c
NODE_TEXT_RADIAL_GRADIENT = 1034
```

**Description**

Sets a radial gradient effect for text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>.</li> <li>.value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[2].f32: radius of the radial gradient. The default value is <b>0</b>.</li> <li>.value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 20

### NODE_TEXT_VERTICAL_ALIGN

```c
NODE_TEXT_VERTICAL_ALIGN = 1035
```

**Description**

Sets the vertical alignment of the text content. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment of the text content, specified using the [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment) enum. The default value is <b>ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment of the text content, specified using the [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment) enum.</li> </ul>

**Since**: 20

### NODE_TEXT_CONTENT_ALIGN

```c
NODE_TEXT_CONTENT_ALIGN = 1036
```

**Description**

Sets the content align of the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: content align of the text, specified using the [ArkUI_TextContentAlign](capi-text-common-h.md#arkui_textcontentalign) enum. The default value is <b>ARKUI_TEXT_CONTENT_ALIGN_CENTER</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: content align of the text, specified using the [ArkUI_TextContentAlign](capi-text-common-h.md#arkui_textcontentalign) enum.</li> </ul>

**Since**: 21

### NODE_TEXT_MIN_LINES

```c
NODE_TEXT_MIN_LINES = 1037
```

**Description**

Sets the minimum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: minimum number of lines in the text.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: minimum number of lines in the text.</li> </ul>

**Since**: 22

### NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR = 1038
```

**Description**

Enables the selected data detector.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Enable selected text recognition, default value true.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether selected text recognition is enabled.</li> </ul>

**Since**: 22

### NODE_TEXT_MIN_LINE_HEIGHT

```c
NODE_TEXT_MIN_LINE_HEIGHT = 1040
```

**Description**

Defines the minimum text line height attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum line height.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum line height.</li> </ul>

**Since**: 22

### NODE_TEXT_MAX_LINE_HEIGHT

```c
NODE_TEXT_MAX_LINE_HEIGHT = 1041
```

**Description**

Defines the maximum text line height attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum line height.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum line height.</li> </ul>

**Since**: 22

### NODE_TEXT_LINE_HEIGHT_MULTIPLE

```c
NODE_TEXT_LINE_HEIGHT_MULTIPLE = 1042
```

**Description**

Defines line height multiple value of text, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: line height multiple value of text.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: line height multiple value of text.</li> </ul>

**Since**: 22

### NODE_TEXT_LAYOUT_MANAGER

```c
NODE_TEXT_LAYOUT_MANAGER = 1043
```

**Description**

Get the text layout manager of the text.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: the layout manager of text. The parameter type is [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md).</li> </ul>

**Since**: 22

### NODE_TEXT_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDIT_MENU_OPTIONS = 1044
```

**Description**

Set the edit menu options of the text.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the edit menu options of text. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).</li> </ul>

**Since**: 22

### NODE_TEXT_BIND_SELECTION_MENU

```c
NODE_TEXT_BIND_SELECTION_MENU = 1045
```

**Description**

Bind the selection menu for text.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the custom selection menu of text. The parameter type is {@link ArkUI_SelectionMenuOptions}.</li> </ul>

**Since**: 22

### NODE_TEXT_TEXT_SELECTION

```c
NODE_TEXT_TEXT_SELECTION = 1046
```

**Description**

Sets the text selection area, which will be highlighted. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: start position of the text selection.</li> <li>.value[1].i32: end position of the text selection.</li> <li>.object: selection options including the menu popup policy. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: start position of the text selection.</li> <li>.value[1].i32: end position of the text selection.</li> <li>.object: selection options including the menu popup policy. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).</li> </ul>

**Since**: 23

### NODE_TEXT_ORPHAN_CHAR_OPTIMIZATION

```c
	  NODE_TEXT_ORPHAN_CHAR_OPTIMIZATION = 1047
```

**Description**

Whether to avoid an orphan word on the last line of the paragraph.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The current state of this feature.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_COMPRESS_LEADING_PUNCTUATION = 1048
```

**Description**

Whether to compress punctuation at the beginning of line.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether compress punctuation at the beginning of line.</li> </ul>

**Since**: 23

### NODE_TEXT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INCLUDE_FONT_PADDING = 1049
```

**Description**

Determines whether the layout adds extra padding at the top and bottom to make space for characters.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Enable include the font padding, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether include the font padding.</li> </ul>

**Since**: 23

### NODE_TEXT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_FALLBACK_LINE_SPACING = 1050
```

**Description**

Whether to include ascent/descent from fallback fonts to prevent overlapping lines.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether fallback line spacing.</li> </ul>

**Since**: 23

### NODE_TEXT_MARQUEE_OPTIONS

```c
NODE_TEXT_MARQUEE_OPTIONS = 1051
```

**Description**

Set the marquee options of text.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the marquee options of text. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: the marquee options of text. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).</li> </ul>

**Since**: 23

### NODE_TEXT_DIRECTION

```c
NODE_TEXT_DIRECTION = 1052
```

**Description**

Writing direction of the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul>

**Since**: 23

### NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE = 1053
```

**Description**

Used to set the selected drag preview style. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul>

**Since**: 23

### NODE_TEXT_CONTROLLER

```c
NODE_TEXT_CONTROLLER = 1054
```

**Description**

Sets the controller of the text.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the controller of the text. The parameter type is [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md).</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_PUNCTUATION_OVERFLOW = 1055
```

**Description**

Sets whether to enable punctuation overflow at line ends. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_TAIL_INDENTS

```c
NODE_TEXT_TAIL_INDENTS = 1056
```

**Description**

Defines the tail indentation for each line in a text block. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: tail indent value, in fp. When size is 1, all lines share the same tail indent.</li> <li>.size: number of tail indent values. When size > 1, the i-th value specifies the tail indent for the i-th line. If the number of text lines exceeds size, the last value is used for the remaining lines.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: first tail indent value, in fp.</li> <li>.size: number of tail indent values.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_STROKE_WIDTH

```c
NODE_TEXT_STROKE_WIDTH = 1057
```

**Description**

Sets the text stroke width. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: text stroke width, in vp. The default value is <b>0</b>, indicating no stroke. A value less than <b>0</b> indicates solid text; a value greater than <b>0</b> indicates outlined text. Percentage values are not supported.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: text stroke width, in vp.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_STROKE_COLOR

```c
NODE_TEXT_STROKE_COLOR = 1058
```

**Description**

Sets the text stroke color. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: text stroke color, in 0xARGB format. The default value is the text font color. Invalid values are treated as the default value.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: text stroke color, in 0xARGB format.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_STROKE_JOIN_STYLE

```c
NODE_TEXT_STROKE_JOIN_STYLE = 1059
```

**Description**

Sets the join style of the text stroke. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text stroke join style. The parameter type is [OH_ArkUI_StrokeJoinStyle](capi-text-common-h.md#oh_arkui_strokejoinstyle). The default value is <b>OH_ARKUI_STROKE_JOIN_STYLE_MITER_JOIN</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text stroke join style. The parameter type is [OH_ArkUI_StrokeJoinStyle](capi-text-common-h.md#oh_arkui_strokejoinstyle).</li> </ul>

**Since**: 26.2.0

### NODE_SPAN_CONTENT

```c
NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SPAN
```

**Description**

Defines the text content attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: content of the text span.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: content of the text span.</li> </ul>

**Since**: 12

### NODE_SPAN_TEXT_BACKGROUND_STYLE

```c
NODE_SPAN_TEXT_BACKGROUND_STYLE
```

**Description**

Defines the text background style. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the text background, in 0xARGB format, for example, <b>0xFFFF0000</b> indicating red. The second parameter indicates the rounded corners of the text background. Two setting modes are available: 1: .value[1].f32: radius of the four corners, in vp. 2: .value[1].f32: radius of the upper left corner, in vp.</li> <li>.value[2].f32: radius of the upper right corner, in vp.</li> <li>.value[3].f32: radius of the lower left corner, in vp.</li> <li>.value[4].f32: radius of the lower right corner, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the text background, in 0xARGB format.</li> <li>.value[1].f32: radius of the upper left corner, in vp.</li> <li>.value[2].f32: radius of the upper right corner, in vp.</li> <li>.value[3].f32: radius of the lower left corner, in vp.</li> <li>.value[4].f32: radius of the lower right corner, in vp.</li> </ul>

**Since**: 12

### NODE_SPAN_BASELINE_OFFSET

```c
NODE_SPAN_BASELINE_OFFSET
```

**Description**

Defines the text baseline offset attribute This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul>

**Since**: 12

### NODE_SPAN_FONT

```c
NODE_SPAN_FONT = 2003
```

**Description**

Defines the text style attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>?.string: font family. Optional. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1]?.i32: font weight. Optional.</li> <li>.value[2]?.i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> <li>?.object: Optional. The font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight.</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> <li>.object: the font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).</li> </ul>

**Since**: 24

### NODE_SPAN_FONT_WEIGHT

```c
NODE_SPAN_FONT_WEIGHT = 2004
```

**Description**

Defines the font weight attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font weight. The default value is 400.</li> <li>?.object: Optional. The font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font weight.</li> <li>.object: the font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).</li> </ul>

**Since**: 24

### NODE_IMAGE_SPAN_SRC

```c
NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_SPAN
```

**Description**

Defines the image source of the image span. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: image address of the image span.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: image address of the image span.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT

```c
NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT
```

**Description**

Defines the alignment mode of the image with the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode of the image with the text. The value is an enum of [ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode of the image with the text. The value is an enum of [ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment).</li> </ul>

**Since**: 12

### NODE_IMAGE_SPAN_ALT

```c
NODE_IMAGE_SPAN_ALT
```

**Description**

Defines the placeholder image source. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: placeholder image source.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: placeholder image source.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_SPAN_BASELINE_OFFSET

```c
NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003
```

**Description**

Defines the baseline offset attribute of the <b>ImageSpan</b> component. This attribute can be set, reset, and obtained as required through APIs. A positive value means an upward offset, while a negative value means a downward offset. The default value is <b>0</b>, and the unit is fp. <br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul>

**Since**: 13

### NODE_IMAGE_SPAN_COLOR_FILTER

```c
NODE_IMAGE_SPAN_COLOR_FILTER = 3004
```

**Description**

Defines the color filter of the image span. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32 to .value[19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: the pointer to OH_Drawing_ColorFilter. Either .value or .object is set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32 to .value [19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: the pointer to OH_Drawing_ColorFilter.</li> </ul>

**Since**: 22

### NODE_IMAGE_SPAN_SUPPORT_SVG2

```c
NODE_IMAGE_SPAN_SUPPORT_SVG2 = 3005
```

**Description**

Set the range of SVG parsing capabilities supported through enable switch. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether color fliter support svg. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: enable switch.</li> </ul>

**Since**: 22

### NODE_IMAGE_SPAN_RESIZABLE

```c
NODE_IMAGE_SPAN_RESIZABLE = 3006
```

**Description**

Resizes the image span when stretching it with array or a lattice object. This attribute can be set, reset, and obtained as required through APIs. The parameter types for setting and getting should be the same.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: width of the left edge, in vp.</li><br><li>.value[1].f32: width of the top edge, in vp.</li><br><li>.value[2].f32: width of the right edge, in vp.</li><br><li>.value[3].f32: width of the bottom edge, in vp.</li><br><li>.object: The parameter type is {@link OH_Drawing_Lattice}.</li><br></ul><br>**Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul><br><li>.value[0].f32: width of the left edge, in vp.</li><br><li>.value[1].f32: width of the top edge, in vp.</li><br><li>.value[2].f32: width of the right edge, in vp.</li><br><li>.value[3].f32: width of the bottom edge, in vp.</li> <li>.object: The parameter type is {@link OH_Drawing_Lattice}.</li> </ul>

**Since**: 26.0.1


