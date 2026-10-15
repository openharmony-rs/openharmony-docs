# Text Display

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

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

Font color attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: font color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: font color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_FONT_SIZE

```c
NODE_FONT_SIZE
```

**Description**

Font size attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: font size, in fp. Value range: [0, +∞). If a negative value is passed, the setting does not take effect. Default value: **16fp**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: font size, in fp.</li> </ul>

**Since**: 12

### NODE_FONT_STYLE

```c
NODE_FONT_STYLE
```

**Description**

Font style attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> </ul>

**Since**: 12

### NODE_FONT_WEIGHT

```c
NODE_FONT_WEIGHT
```

**Description**

Font weight attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). A larger value indicates a bolder font. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul>

**Since**: 12

### NODE_TEXT_LINE_HEIGHT

```c
NODE_TEXT_LINE_HEIGHT
```

**Description**

Text line height attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: line height, in fp. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: line height, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_DECORATION

```c
NODE_TEXT_DECORATION
```

**Description**

Text decorative line style and its color. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for adding text decoration effects, such as underlines for links, strikethroughs for deleted content, or overlines for emphasis. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text decorative line type. The value is an enumerated value of [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype). Default value: <b>ARKUI_TEXT_DECORATION_TYPE_NONE</b>, indicating no decorative line.</li> <li>.value[1]?.u32: text decorative line color, in 0xARGB format. For example, **0xFFFF0000** indicates red. This parameter is optional. Default value: <b>0xFF000000</b>, indicating black.</li> <li>.value[2]?.i32: text decorative line style. The value is an enumerated value of [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle). Default value: <b>ARKUI_TEXT_DECORATION_STYLE_SOLID</b>, indicating a solid decorative line.</li> <li>.value[3]?.f32: thickness of the text decorative line. This parameter is optional. The default value is <b>1.0</b>. The value range is [0, +∞). If a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text decorative line type. The value is an enumerated value of [ArkUI_TextDecorationType](capi-text-common-h.md#arkui_textdecorationtype).</li> <li>.value[1].u32: text decorative line color, in 0xARGB format.</li> <li>.value[2].i32: text decorative line style. The value is an enumerated value of [ArkUI_TextDecorationStyle](capi-text-common-h.md#arkui_textdecorationstyle).</li> <li>.value[3].f32: thickness of the text decorative line.</li> </ul>

**Since**: 12

### NODE_TEXT_CASE

```c
NODE_TEXT_CASE
```

**Description**

Text case attribute, which can be set, reset, and obtained as required through APIs. This attribute is suitable for controlling the text display format, such as automatically capitalizing titles or formatting user input to a uniform case. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text case. The parameter type is [ArkUI_TextCase](capi-text-common-h.md#arkui_textcase). The default value is <b>ARKUI_TEXT_CASE_NORMAL</b>, which indicates that the original case is retained.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text case. The parameter type is [ArkUI_TextCase](capi-text-common-h.md#arkui_textcase).</li> </ul>

**Since**: 12

### NODE_TEXT_LETTER_SPACING

```c
NODE_TEXT_LETTER_SPACING
```

**Description**

Letter spacing attribute, which can be set, reset, and obtained as required through APIs. This attribute is suitable for adjusting text layout effects, such as setting title letter spacing to enhance visual effects or adjusting the layout aesthetics of special text styles. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: letter spacing, in fp. Value range: (-∞, +∞). When the value is negative, the text is compressed. If the negative value is too small, the component content area size is compressed to 0, causing the content to be undisplayable.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: letter spacing, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_MAX_LINES

```c
NODE_TEXT_MAX_LINES
```

**Description**

Maximum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: maximum number of lines. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: maximum number of lines.</li> </ul>

**Since**: 12

### NODE_TEXT_ALIGN

```c
NODE_TEXT_ALIGN
```

**Description**

Horizontal alignment mode of the text. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: horizontal alignment mode of the text. The value is an enumerated value of [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment). The default value is <b>ARKUI_TEXT_ALIGNMENT_START</b>, which indicates alignment with the start edge.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: horizontal alignment mode of the text. The value is an enumerated value of [ArkUI_TextAlignment](capi-text-common-h.md#arkui_textalignment).</li> </ul>

**Since**: 12

### NODE_TEXT_OVERFLOW

```c
NODE_TEXT_OVERFLOW
```

**Description**

Text overflow attribute, which can be set, reset, and obtained as required through APIs. This attribute is suitable for scenarios where text content exceeds the display area, such as using an ellipsis for a single-line title or truncating card content. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). The default value is <b>ARKUI_TEXT_OVERFLOW_NONE</b>, which indicates the text is displayed without clipping when it exceeds the limit.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).</li> </ul>

**Since**: 12

### NODE_FONT_FAMILY

```c
NODE_FONT_FAMILY
```

**Description**

Font family attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: font string. Multiple fonts are separated by commas (,). The system default font is used when no value is passed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font string. Multiple fonts are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_COPY_OPTION

```c
NODE_TEXT_COPY_OPTION
```

**Description**

Copy option attribute, which can be set, reset, and obtained as required through APIs. This attribute is suitable for controlling text copy and paste behavior, such as prohibiting copying in a password input box or protecting sensitive information. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is <b>ARKUI_COPY_OPTIONS_NONE</b>, which indicates that copying is not supported.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions).</li> </ul>

**Since**: 12

### NODE_TEXT_BASELINE_OFFSET

```c
NODE_TEXT_BASELINE_OFFSET
```

**Description**

Text baseline offset attribute, which can be set, reset, and obtained as required through APIs. This attribute is suitable for adjusting the text baseline position, such as adjusting the offset when displaying superscripts and subscripts, or achieving precise alignment between text and images in mixed layouts. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: baseline offset, in fp. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_TEXT_SHADOW

```c
NODE_TEXT_TEXT_SHADOW
```

**Description**

Text shadow attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: blur radius of the shadow, in vp. Value range: [0, +∞). The default value is <b>0</b>, indicating no blur effect.</li> <li>.value[1].i32: shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype). The default value is <b>ARKUI_SHADOW_TYPE_COLOR</b>, indicating a color shadow.</li> <li>.value[2].u32: shadow color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> <li>.value[3].f32: offset of the shadow along the x-axis, in vp.</li> <li>.value[4].f32: offset of the shadow along the y-axis, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: blur radius of the shadow, in vp.</li> <li>.value[1].i32: shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype).</li> <li>.value[2].u32: shadow color, in 0xARGB format.</li> <li>.value[3].f32: offset of the shadow along the x-axis, in vp.</li> <li>.value[4].f32: offset of the shadow along the y-axis, in vp.</li> </ul>

**Since**: 12

### NODE_TEXT_MIN_FONT_SIZE

```c
NODE_TEXT_MIN_FONT_SIZE
```

**Description**

Minimum font size attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum font size, in fp. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum font size, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_MAX_FONT_SIZE

```c
NODE_TEXT_MAX_FONT_SIZE
```

**Description**

Maximum font size attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum font size, in fp. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum font size, in fp.</li> </ul>

**Since**: 12

### NODE_TEXT_FONT

```c
NODE_TEXT_FONT
```

**Description**

Text style attribute, which can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string?: font family. This parameter is optional. Use commas (,) to separate multiple fonts. The system default font is used when this parameter is not passed.</li> <li>.value[0].f32: text size, in fp. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> <li>.value[1]?.i32: font weight. This parameter is optional. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). A larger value indicates a bolder font. Default value: <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> <li>.value[2]?.i32: font style. This parameter is optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). Default value: <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: text size, in fp. Value range: [0, +∞).</li> <li>.value[1].i32: font weight. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). Default value: <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). Default value: <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_HEIGHT_ADAPTIVE_POLICY

```c
NODE_TEXT_HEIGHT_ADAPTIVE_POLICY
```

**Description**

How the adaptive height is determined for the text. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for scenarios where text content changes dynamically, such as prioritizing the maximum line count to limit height or prioritizing the minimum font size to ensure text readability. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: how the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-text-h.md#arkui_textheightadaptivepolicy). Default value: <b>ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST</b>, indicating **MaxLines** takes precedence.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: how the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-text-h.md#arkui_textheightadaptivepolicy).</li> </ul>

**Since**: 12

### NODE_TEXT_INDENT

```c
NODE_TEXT_INDENT
```

**Description**

Indentation of the first line. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: indentation of the first line. The input parameter unit is fp, and the return value unit is vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: indentation of the first line. The input parameter unit is fp, and the return value unit is vp.</li> </ul>

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

Ellipsis position. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for controlling the display position of the text ellipsis, such as trailing ellipsis for regular text, leading ellipsis for path display, and middle ellipsis for long titles. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode). The default value is <b>ARKUI_ELLIPSIS_MODE_END</b>, indicating that content at the end of the line is ellipsized.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode).</li> </ul>

**Since**: 12

### NODE_TEXT_LINE_SPACING

```c
NODE_TEXT_LINE_SPACING
```

**Description**

Defines the text line spacing attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: line spacing, in fp.</li> <li>?.object: Optional. Pointer to [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object for line spacing options. Available since API version 26.2.0. Use [OH_ArkUI_NativeModule_LineSpacingOptions_Create](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_create) to create and [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy the object.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: line spacing, in fp.</li> <li>.object: pointer to [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object for line spacing options. Available since API version 26.2.0.</li> </ul>

**Since**: 12

### NODE_FONT_FEATURE

```c
NODE_FONT_FEATURE
```

**Description**

Font feature. **NODE_FONT_FEATURE** provides advanced typographic features in OpenType fonts. These features such as ligatures and monospace are generally used in custom fonts and require support from the respective fonts. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: string that describes the font feature settings. The value format is <b>normal \| &lt;feature-tag-value&gt;</b>. Syntax for <b>&lt;feature-tag-value&gt;</b> is <b>&lt;string&gt; [ &lt;integer&gt; \| on \| off]</b>. There can be multiple <b>&lt;feature-tag-value&gt;</b> values, separated by commas (,). For example, for the monospace feature, you can pass in <b>ss01 on</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font feature. Multiple font features are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_ENABLE_DATA_DETECTOR
```

**Description**

Whether to enable text entity recognition. The recognized entity types can be configured through the **NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG** attribute. This attribute is suitable for recognizing specific entity types in text (such as phone numbers, email addresses, and URLs) to implement features like tap-to-redirection and smart interaction. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable text entity recognition. The value <b>1</b> means to enable text entity recognition, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether text entity recognition is enabled. The value <b>1</b> means that text entity recognition is enabled, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG
```

**Description**

Text recognition configuration. This attribute is suitable for customizing the entity types to be recognized (such as phone numbers, email addresses, and URLs) to implement precise text smart recognition and interaction features. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0...].i32: entity type array. The parameter type is [ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype). The array can contain entity types such as phone numbers, URLs, and email addresses. For specific values, refer to the enumeration definition. This parameter takes effect only when **NODE_TEXT_ENABLE_DATA_DETECTOR** is set to <b>1</b> (text entity recognition enabled).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0...].i32: entity type array. The parameter type is [ArkUI_TextDataDetectorType](capi-text-h.md#arkui_textdatadetectortype).</li> </ul>

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

String to use in the styled string. This attribute can be set, reset, and obtained as required through APIs. Configuring a custom [OH_Drawing_Typography](../../apis-arkgraphics2d/c-apis/capi-drawing-oh-drawing-typography.md) object for the **Text** component will skip the layout measurement phase of the component. Note the following: 1. Ensure that the lifecycles of the **OH_ArkUI_StyledString** object and **OH_Drawing_Typography** object are aligned with the lifecycle of the **Text** component. Reset the **OH_ArkUI_StyledString** object when the **Text** component is destroyed; otherwise, it may lead to null pointer crashes in the application. 2. Ensure that the **OH_Drawing_TypographyLayout** API is called prior to the layout measurement of the **Text** component. 3. When the **OH_ArkUI_StyledString** and **OH_Drawing_Typography** objects are released, the **reset** API of the **Text** component must be called synchronously; otherwise, it may cause null pointer crashes in the application. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: string to use in the styled string. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: string to use in the styled string. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).</li> </ul>

**Since**: 12

### NODE_TEXT_HALF_LEADING

```c
NODE_TEXT_HALF_LEADING = 1029
```

**Description**

Whether to center text vertically in the **Text** component.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to center text vertically. The default value is **0**. The value **1** means to center text vertically, and **0** means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the text is vertically centered. The value **1** means the text is vertically centered, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_IMMUTABLE_FONT_WEIGHT

```c
NODE_IMMUTABLE_FONT_WEIGHT = 1030
```

**Description**

Font weight attribute, which can be set, reset, and obtained as required through APIs. The font weight specified by this API is not affected by any changes in the system font weight settings. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). A larger value indicates a bolder font. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul>

**Since**: 15

### NODE_TEXT_LINE_COUNT

```c
NODE_TEXT_LINE_COUNT = 1031
```

**Description**

Number of lines in the text. This attribute can be obtained as required through APIs. The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of lines in the text.</li> </ul>

**Since**: 20

### NODE_TEXT_OPTIMIZE_TRAILING_SPACE

```c
NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032
```

**Description**

Whether to optimize the trailing spaces at the end of each line during text layout. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for optimizing text layout effects, such as removing extra trailing spaces to achieve better text alignment. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to optimize the trailing spaces at the end of each line during text layout. The default value is <b>0</b>. The value <b>1</b> means to optimize trailing spaces at the end of each line during text layout, and <b>0</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the trailing spaces at the end of each line are optimized during text layout. The value <b>1</b> indicates the trailing spaces at the end of each line are optimized during text layout, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 20

### NODE_TEXT_LINEAR_GRADIENT

```c
NODE_TEXT_LINEAR_GRADIENT = 1033
```

**Description**

Linear gradient effect for text. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: start angle of the linear gradient. The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>; otherwise, the <b>direction</b> attribute serves as the primary layout method. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>.</li> <li>.value[1].i32: direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). When a direction other than <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> attribute is ignored. The default value is <b>ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM</b>.</li> <li>.value[2].i32: whether to repeat the colors. The value <b>1</b> means to repeat the gradient colors, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> <li>.object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red. stops: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value. size: number of colors. If the value is smaller than the length of the <b>colors</b> array, only the first <b>size</b> colors take effect. Values greater than the <b>colors</b> array length, values less than or equal to 0, or invalid values are not recommended.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: start angle of the linear gradient. The set value is used only when <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is used. In other cases, the default value <b>0</b> is used.</li> <li>.value[1].i32: direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).</li> <li>.value[2].i32: whether the colors are repeated. The value <b>0</b> means that the colors are not repeated, and <b>1</b> means the opposite. The default value is <b>0</b>.</li> <li>.object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red. stops: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. size: number of effective gradient colors.</li> </ul>

**Since**: 20

### NODE_TEXT_RADIAL_GRADIENT

```c
NODE_TEXT_RADIAL_GRADIENT = 1034
```

**Description**

Radial gradient effect for text. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. Default value: <b>0</b>.</li> <li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. The coordinates of the upper left corner of the text box are [0, 0]. Default value: <b>0</b>.</li> <li>.value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> <li>.value[3]?.i32: whether to repeat the colors. The value <b>1</b> indicates to repeat the colors, and <b>0</b> indicates the opposite. Default value: <b>0</b>.</li> <li>.object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red. stops: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value. size: number of colors. If the value is smaller than the length of the <b>colors</b> array, only the first <b>size</b> colors take effect. Values greater than the <b>colors</b> array length, values less than or equal to 0, or invalid values are not recommended.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp.</li> <li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. The coordinates of the upper left corner of the text box are [0, 0].</li> <li>.value[2]?.f32: radius of the radial gradient, in vp. The default value is <b>0</b>.</li> <li>.value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> <li>.object: the parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. colors: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red. stops: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. size: number of effective gradient colors.</li> </ul>

**Since**: 20

### NODE_TEXT_VERTICAL_ALIGN

```c
NODE_TEXT_VERTICAL_ALIGN = 1035
```

**Description**

Vertical alignment mode of the text content. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment mode of the text content. The parameter type is [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment). The default value is <b>ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment mode of the text content. The parameter type is [ArkUI_TextVerticalAlignment](capi-text-common-h.md#arkui_textverticalalignment).</li> </ul>

**Since**: 20

### NODE_TEXT_CONTENT_ALIGN

```c
NODE_TEXT_CONTENT_ALIGN = 1036
```

**Description**

Vertical alignment mode of the text content area. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: vertical alignment mode of the text content area. The parameter type is [ArkUI_TextContentAlign](capi-text-common-h.md#arkui_textcontentalign). The default value is <b>ARKUI_TEXT_CONTENT_ALIGN_CENTER</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: vertical alignment mode of the text content area. The parameter type is [ArkUI_TextContentAlign](capi-text-common-h.md#arkui_textcontentalign).</li> </ul>

**Since**: 21

### NODE_TEXT_MIN_LINES

```c
NODE_TEXT_MIN_LINES = 1037
```

**Description**

Minimum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: minimum number of lines in the text. Value range: positive integer. The setting does not take effect when 0 or a negative value is passed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: minimum number of lines in the text. Value range: positive integer.</li> </ul>

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

Minimum line height. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for limiting the minimum text line height, such as ensuring text readability or preventing overlapping text display caused by an excessively small line height. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: minimum line height of the text. Default value: <b>0</b>. Unit: fp. Value range: [0, +∞). When a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: minimum line height of the text. The unit is fp.</li> </ul>

**Since**: 22

### NODE_TEXT_MAX_LINE_HEIGHT

```c
NODE_TEXT_MAX_LINE_HEIGHT = 1041
```

**Description**

Maximum line height. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for limiting the maximum text line height, such as controlling the compactness of text layout or preventing wasted display space caused by an excessively large line height. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: maximum line height of the text. Default value: <b>0</b>, which indicates that the maximum line height is not limited. The unit is fp. Value range: [0, +∞). If a negative value is passed, the setting does not take effect.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: maximum line height of the text. The unit is fp.</li> </ul>

**Since**: 22

### NODE_TEXT_LINE_HEIGHT_MULTIPLE

```c
NODE_TEXT_LINE_HEIGHT_MULTIPLE = 1042
```

**Description**

Multiple value of the multiple line height mode. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for setting the line height relative to the font size, such as implementing dynamic layout or automatically adjusting the line height when the font size changes.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: line height multiple value of text.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: line height multiple value of text.</li> </ul>

**Since**: 22

### NODE_TEXT_LAYOUT_MANAGER

```c
NODE_TEXT_LAYOUT_MANAGER = 1043
```

**Description**

Text layout manager. This attribute can be obtained as required through APIs. This attribute is suitable for obtaining text layout information, such as querying the number of text lines and character positions, as well as measuring text sizes.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: the layout manager of text. The parameter type is [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md).</li> </ul>

**Since**: 22

### NODE_TEXT_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDIT_MENU_OPTIONS = 1044
```

**Description**

Extended options of the text menu. This attribute can be set as required through APIs. This attribute is suitable for extending the text editing menu, such as adding custom action items or extending copy and paste functions.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the edit menu options of text. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).</li> </ul>

**Since**: 22

### NODE_TEXT_BIND_SELECTION_MENU

```c
NODE_TEXT_BIND_SELECTION_MENU = 1045
```

**Description**

Custom text selection menu. This attribute can be set as required through APIs. This attribute is suitable for customizing the text selection menu, such as adding specific action buttons or customizing the menu UI style.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the custom selection menu of text. The parameter type is ArkUI_SelectionMenuOptions.</li> </ul>

**Since**: 22

### NODE_TEXT_TEXT_SELECTION

```c
NODE_TEXT_TEXT_SELECTION = 1046
```

**Description**

Text selection area, which will be highlighted, for the component that obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Start position of the text selection. Value range: [0, Text length]. The value must be a valid text index.</li> <li>.value[1].i32: End position of the text selection. Value range: [0, Text length]. The value must be a valid text index.</li> <li>.object: Selection options. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Start position of the text selection.</li> <li>.value[1].i32: End position of the text selection.</li> <li>.object: Selection options. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).</li> </ul>

**Since**: 23

### NODE_TEXT_ORPHAN_CHAR_OPTIMIZATION

```c
	  NODE_TEXT_ORPHAN_CHAR_OPTIMIZATION = 1047
```

**Description**

Whether to enable orphan character optimization for text layout in the **Text** component. When set, the orphan character (the first character in the last line of a paragraph) is processed more efficiently to improve the text layout. When enabled, it adjusts line break positions to avoid orphan characters as much as possible. The orphan character optimization feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The current state of this feature.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_COMPRESS_LEADING_PUNCTUATION = 1048
```

**Description**

Whether to enable leading punctuation compression. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for Chinese layout scenarios, compressing leading punctuations to improve layout aesthetics and reading experience.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether compress punctuation at the beginning of line.</li> </ul>

**Since**: 23

### NODE_TEXT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INCLUDE_FONT_PADDING = 1049
```

**Description**

Whether to add spacing to the first and last lines to avoid text truncation.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Enable include the font padding, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether include the font padding.</li> </ul>

**Since**: 23

### NODE_TEXT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_FALLBACK_LINE_SPACING = 1050
```

**Description**

Whether the line height can be automatically adjusted based on the actual text height for multi-line text overlay. This enumerated value takes effect only when the line height is smaller than the actual text height.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether fallback line spacing.</li> </ul>

**Since**: 23

### NODE_TEXT_MARQUEE_OPTIONS

```c
NODE_TEXT_MARQUEE_OPTIONS = 1051
```

**Description**

Configuration options of the text marquee mode. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for long text scrolling display scenarios, such as notification reminders and scrolling title display.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the marquee options of text. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: the marquee options of text. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).</li> </ul>

**Since**: 23

### NODE_TEXT_DIRECTION

```c
NODE_TEXT_DIRECTION = 1052
```

**Description**

Text layout direction. This attribute is suitable for supporting the layout requirements of different languages, such as right-to-left (RTL) language display for Arabic and Hebrew.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul>

**Since**: 23

### NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE = 1053
```

**Description**

Drag preview style when the text is selected.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul>

**Since**: 23

### NODE_TEXT_CONTROLLER

```c
NODE_TEXT_CONTROLLER = 1054
```

**Description**

Text controller. This attribute is suitable for managing text editing behavior, such as controlling text display and managing formatted strings.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the controller of the text. The parameter type is [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md).</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_PUNCTUATION_OVERFLOW = 1055
```

**Description**

Whether to enable punctuation hanging at the end of a line for the Text component. This attribute can be set, reset, and obtained as required through APIs. This attribute is suitable for Chinese layout scenarios, displaying trailing punctuation outside the line to optimize the layout effect.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_TAIL_INDENTS

```c
NODE_TEXT_TAIL_INDENTS = 1056
```

**Description**

Tail indentation of each line in a text block. This attribute is suitable for implementing special layout effects, such as poetry layout and quoted text alignment, which require controlling the trailing space of each line.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: tail indent value, in fp. When size is 1, all lines share the same tail indent.</li> <li>.size: number of tail indent values. When size > 1, the i-th value specifies the tail indent for the i-th line. If the number of text lines exceeds size, the last value is used for the remaining lines.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: first tail indent value, in fp.</li> <li>.size: number of tail indent values.</li> </ul>

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

Text background style. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the text background, in 0xARGB format, for example, <b>0xFFFF0000</b> indicating red. The second parameter indicates the rounded corners of the text background. Two setting modes are available: 1: .value[1].f32: radius of the four corners, in vp. 2: .value[1].f32: radius of the upper left corner, in vp.</li> <li>.value[2].f32: radius of the upper right corner, in vp.</li> <li>.value[3].f32: radius of the lower left corner, in vp.</li> <li>.value[4].f32: radius of the lower right corner, in vp.</li> <li>.value[5]?.f32: border width of the text background, in vp. Optional. The default value is <b>0</b>. This parameter is supported since API version 26.2.0.</li> <li>.value[6]?.u32: border color of the text background, in 0xARGB format. Optional. The default value is <b>0x00000000</b> (transparent). This parameter is supported since API version 26.2.0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the text background, in 0xARGB format.</li> <li>.value[1].f32: radius of the upper left corner, in vp.</li> <li>.value[2].f32: radius of the upper right corner, in vp.</li> <li>.value[3].f32: radius of the lower left corner, in vp.</li> <li>.value[4].f32: radius of the lower right corner, in vp.</li> <li>.value[5].f32: border width of the text background, in vp. This parameter is supported since API version 26.2.0.</li> <li>.value[6].u32: border color of the text background, in 0xARGB format. This parameter is supported since API version 26.2.0.</li> </ul>

**Since**: 12

### NODE_SPAN_BASELINE_OFFSET

```c
NODE_SPAN_BASELINE_OFFSET
```

**Description**

Text baseline offset attribute, which can be set, reset, and obtained as required through APIs. This attribute is suitable for adjusting the baseline position of the text of the **Span** component, such as displaying superscripts and subscripts or implementing special layout effects.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul>

**Since**: 12

### NODE_SPAN_FONT

```c
NODE_SPAN_FONT = 2003
```

**Description**

Text style attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>?.string: font family. Optional. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1]?.i32: font weight. Optional.</li> <li>.value[2]?.i32: font style. Optional. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> <li>?.object: Optional. The font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: font family. Use commas (,) to separate multiple fonts.</li> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font weight.</li> <li>.value[2].i32: font style. The parameter type is [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> <li>.object: the font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).</li> </ul>

**Since**: 24

### NODE_SPAN_FONT_WEIGHT

```c
NODE_SPAN_FONT_WEIGHT = 2004
```

**Description**

Font weight attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: font weight. The default value is 400.</li> <li>?.object: Optional. The font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: font weight.</li> <li>.object: the font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).</li> </ul>

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

Alignment mode of the image with the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode of the image with the text. The value is an enum of [ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode of the image with the text. The value is an enum of [ArkUI_ImageSpanAlignment](capi-image-span-h.md#arkui_imagespanalignment).</li> </ul>

**Since**: 12

### NODE_IMAGE_SPAN_ALT

```c
NODE_IMAGE_SPAN_ALT
```

**Description**

Placeholder image address for the image span. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: placeholder image source.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: placeholder image source.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_SPAN_BASELINE_OFFSET

```c
NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003
```

**Description**

Baseline offset attribute of the **ImageSpan** component. This attribute can be set, reset, and obtained as required through APIs. A positive value means an upward offset, while a negative value means a downward offset. The default value is **0**, and the unit is fp. This attribute is suitable for adjusting the relative position between images and text in mixed layouts to achieve precise alignment effects.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: baseline offset, in fp.</li> </ul>

**Since**: 13

### NODE_IMAGE_SPAN_COLOR_FILTER

```c
NODE_IMAGE_SPAN_COLOR_FILTER = 3004
```

**Description**

Color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32 to .value[19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: the pointer to OH_Drawing_ColorFilter. Either .value or .object is set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32 to .value [19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: the pointer to OH_Drawing_ColorFilter.</li> </ul>

**Since**: 22

### NODE_IMAGE_SPAN_SUPPORT_SVG2

```c
NODE_IMAGE_SPAN_SUPPORT_SVG2 = 3005
```

**Description**

Whether to enable the new SVG parsing capability, which allows you to set the scope of SVG parsing functionality support. This attribute can be set, reset, and obtained as required through APIs. After the **ImageSpan** component is created, the value of this attribute cannot be dynamically changed.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether color fliter support svg. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: enable switch.</li> </ul>

**Since**: 22

### NODE_IMAGE_SPAN_RESIZABLE

```c
NODE_IMAGE_SPAN_RESIZABLE = 3006
```

**Description**

Resizes the image span when stretching it with array or a lattice object. This attribute can be set, reset, and obtained as required through APIs. The parameter types for setting and getting should be the same.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width of the left edge, in vp.</li> <li>.value[1].f32: width of the top edge, in vp.</li> <li>.value[2].f32: width of the right edge, in vp.</li> <li>.value[3].f32: width of the bottom edge, in vp.</li> <li>.object: The parameter type is [OH_Drawing_Lattice](../../apis-arkgraphics2d/c-apis/capi-drawing-oh-drawing-lattice.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the left edge, in vp.</li> <li>.value[1].f32: width of the top edge, in vp.</li> <li>.value[2].f32: width of the right edge, in vp.</li> <li>.value[3].f32: width of the bottom edge, in vp.</li> <li>.object: The parameter type is [OH_Drawing_Lattice](../../apis-arkgraphics2d/c-apis/capi-drawing-oh-drawing-lattice.md).</li> </ul>

**Since**: 26.2.0


