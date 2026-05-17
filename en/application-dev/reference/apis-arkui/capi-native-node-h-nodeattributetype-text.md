# ArkUI_NodeAttributeType (Text Display Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @kangshihui-->
<!--Designer: @xiangyuan6; @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for text display components including **Text**, **Span**, and **ImageSpan**.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)


## NODE_TEXT_CONTENT

```c
NODE_TEXT_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT = 1000
```

Text content attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Text content.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Text content.|

## NODE_FONT_COLOR

```c
NODE_FONT_COLOR = 1001
```

Font color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Font color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Font color, in 0xARGB format.|

## NODE_FONT_SIZE

```c
NODE_FONT_SIZE = 1002
```

Font size attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Font size, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Font size, in fp.|

## NODE_FONT_STYLE

```c
NODE_FONT_STYLE = 1003
```

Font style attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).|

## NODE_FONT_WEIGHT

```c
NODE_FONT_WEIGHT = 1004
```

Font weight attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

## NODE_TEXT_LINE_HEIGHT

```c
NODE_TEXT_LINE_HEIGHT = 1005
```

Text line height attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Line height, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Line height, in fp.|

## NODE_TEXT_DECORATION

```c
NODE_TEXT_DECORATION = 1006
```

Text decorative line style and its color. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text decorative line type. The parameter type is [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype). The default value is **ARKUI_TEXT_DECORATION_TYPE_NONE**.|
| .value[1]?.u32 | Text decorative line color, in 0xARGB format. For example, **0xFFFF0000** indicates red. This parameter is optional.|
| .value[2]?.i32 | Text decorative line style. The parameter type is [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle).|
| .value[3]?.f32 | Thickness of the text decorative line. This parameter is optional. The default value is **1.0**. The value range is [0, +∞).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text decorative line type. The parameter type is [ArkUI_TextDecorationType](capi-native-type-h.md#arkui_textdecorationtype).|
| .value[1].u32 | Text decorative line color, in 0xARGB format.|
| .value[2].i32 | Text decorative line style. The parameter type is [ArkUI_TextDecorationStyle](capi-native-type-h.md#arkui_textdecorationstyle).|
| .value[3].f32 | Thickness of the text decorative line.|

## NODE_TEXT_CASE

```c
NODE_TEXT_CASE = 1007
```

Text case attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text case. The parameter type is [ArkUI_TextCase](capi-native-type-h.md#arkui_textcase). The default value is **ARKUI_TEXT_CASE_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text case. The parameter type is [ArkUI_TextCase](capi-native-type-h.md#arkui_textcase).|

## NODE_TEXT_LETTER_SPACING

```c
NODE_TEXT_LETTER_SPACING = 1008
```

Letter spacing attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Letter spacing, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Letter spacing, in fp.|

## NODE_TEXT_MAX_LINES

```c
NODE_TEXT_MAX_LINES = 1009
```

Maximum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines.|

## NODE_TEXT_ALIGN

```c
NODE_TEXT_ALIGN = 1010
```

Horizontal alignment mode of the text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the text. The value is an enumerated value of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment). The default value is **ARKUI_TEXT_ALIGNMENT_START**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Horizontal alignment mode of the text. The value is an enumerated value of [ArkUI_TextAlignment](capi-native-type-h.md#arkui_textalignment).|

## NODE_TEXT_OVERFLOW

```c
NODE_TEXT_OVERFLOW = 1011
```

Text overflow attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long, specified using the [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow) enum. The default value is **ARKUI_TEXT_OVERFLOW_NONE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long. The parameter type is [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow).|

## NODE_FONT_FAMILY

```c
NODE_FONT_FAMILY = 1012
```

Font family attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Fonts, separated by commas (,).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Fonts, separated by commas (,).|

## NODE_TEXT_COPY_OPTION

```c
NODE_TEXT_COPY_OPTION = 1013
```

Copy option attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is **ARKUI_COPY_OPTIONS_NONE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions).|

## NODE_TEXT_BASELINE_OFFSET

```c
NODE_TEXT_BASELINE_OFFSET = 1014
```

Text baseline offset attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Baseline offset, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Baseline offset, in fp.|

## NODE_TEXT_TEXT_SHADOW

```c
NODE_TEXT_TEXT_SHADOW = 1015
```

Text shadow attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Blur radius of the shadow, in vp.|
| .value[1].i32 | Shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype). The default value is **ARKUI_SHADOW_TYPE_COLOR**.|
| .value[2].u32 | Shadow color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| .value[3].f32 | Offset of the shadow along the x-axis, in vp.|
| .value[4].f32 | Offset of the shadow along the y-axis, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Blur radius of the shadow, in vp.|
| .value[1].i32 | Shadow type. The parameter type is [ArkUI_ShadowType](capi-native-type-h.md#arkui_shadowtype).|
| .value[2].u32 | Shadow color, in 0xARGB format.|
| .value[3].f32 | Offset of the shadow along the x-axis, in vp.|
| .value[4].f32 | Offset of the shadow along the y-axis, in vp.|

## NODE_TEXT_MIN_FONT_SIZE

```c
NODE_TEXT_MIN_FONT_SIZE = 1016
```

Minimum font size attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum font size, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum font size, in fp.|

## NODE_TEXT_MAX_FONT_SIZE

```c
NODE_TEXT_MAX_FONT_SIZE = 1017
```

Maximum font size attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Maximum font size, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Maximum font size, in fp.|

## NODE_TEXT_FONT

```c
NODE_TEXT_FONT = 1018
```

Text style attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string? | Font family. This parameter is optional. Use commas (,) to separate multiple fonts.|
| .value[0].f32 | Font size, in fp.|
| .value[1]?.i32 | Font weight. This parameter is optional. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.|
| .value[2]?.i32 | Font style. This parameter is optional. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Font family. Use commas (,) to separate multiple fonts.|
| .value[0].f32 | Font size, in fp.|
| .value[1].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.|
| .value[2].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.|

## NODE_TEXT_HEIGHT_ADAPTIVE_POLICY

```c
NODE_TEXT_HEIGHT_ADAPTIVE_POLICY = 1019
```

How the adaptive height is determined for the text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | How the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy). The default value is **ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | How the adaptive height is determined for the text. The parameter type is [ArkUI_TextHeightAdaptivePolicy](capi-native-type-h.md#arkui_textheightadaptivepolicy).|

## NODE_TEXT_INDENT

```c
NODE_TEXT_INDENT = 1020
```

Indentation of the first line. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Indentation of the first line, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Indentation of the first line, in vp.|

## NODE_TEXT_WORD_BREAK

```c
NODE_TEXT_WORD_BREAK = 1021
```

Line break rule. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). The default value is **ARKUI_WORD_BREAK_BREAK_WORD**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak).|

## NODE_TEXT_ELLIPSIS_MODE

```c
NODE_TEXT_ELLIPSIS_MODE = 1022
```

Ellipsis position. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). The default value is **ARKUI_ELLIPSIS_MODE_END**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode).|

## NODE_TEXT_LINE_SPACING

```c
NODE_TEXT_LINE_SPACING = 1023
```

Line spacing attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Line spacing, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Line spacing, in fp.|

## NODE_FONT_FEATURE

```c
NODE_FONT_FEATURE = 1024
```

Font feature. **NODE_FONT_FEATURE** provides advanced typographic features in OpenType fonts. These features such as hyphenation and monospace are generally used in custom fonts and require support from the respective fonts. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | String that describes the font feature settings. The value format is **normal \| &lt;feature-tag-value&gt;**.<br>Syntax for **&lt;feature-tag-value&gt;** is **&lt;string&gt; [ &lt;integer&gt; \| on \| off ]**.<br>There can be multiple **&lt;feature-tag-value&gt;** values, separated by commas (,). For example, for the monospace feature, you can pass in **ss01 on**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Font feature. Multiple font features are separated by commas (,).|

## NODE_TEXT_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_ENABLE_DATA_DETECTOR = 1025
```

Whether to enable text recognition.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable text recognition. The default value is **false**. The value **true** means to enable text recognition, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether text recognition is enabled.|

## NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_ENABLE_DATA_DETECTOR_CONFIG = 1026
```

Text recognition configuration.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0...].i32 | Array of entity types. The parameter type is [ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0...].i32 | Array of entity types. The parameter type is [ArkUI_TextDataDetectorType](capi-native-type-h.md#arkui_textdatadetectortype).|

## NODE_TEXT_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_SELECTED_BACKGROUND_COLOR = 1027
```

Background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_TEXT_CONTENT_WITH_STYLED_STRING

```c
NODE_TEXT_CONTENT_WITH_STYLED_STRING = 1028
```

String to use in the styled string. This attribute can be set, reset, and obtained as required through APIs. Configuring a custom [OH_Drawing_Typography](../apis-arkgraphics2d/capi-drawing-oh-drawing-typography.md) object for the **Text** component will skip the layout measurement phase of the component. Note the following:<br> 1. Ensure that the lifecycles of the **OH_ArkUI_StyledString** object and **OH_Drawing_Typography** object are aligned with the lifecycle of the **Text** component. Reset the **OH_ArkUI_StyledString** object when the **Text** component is destroyed; otherwise, it may lead to null pointer crashes in the application.<br> 2. Ensure that the **OH_Drawing_TypographyLayout** API is called prior to the layout measurement of the **Text** component.<br> 3. When the **OH_ArkUI_StyledString** and **OH_Drawing_Typography** objects are released, the **reset** API of the **Text** component must be called synchronously; otherwise, it may cause null pointer crashes in the application.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | String to use in the styled string. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | String to use in the styled string. The parameter type is [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md).|

## NODE_TEXT_HALF_LEADING

```c
NODE_TEXT_HALF_LEADING = 1029
```

Whether to center text vertically in the **Text** component.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to center text vertically. The default value is **false**.<br>The value **true** means to center text vertically, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text is vertically centered.|

## NODE_IMMUTABLE_FONT_WEIGHT

```c
NODE_IMMUTABLE_FONT_WEIGHT = 1030
```

Font weight attribute, which can be set, reset, and obtained as required through APIs. The font weight specified by this API is not affected by any changes in the system font weight settings.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight). The default value is **ARKUI_FONT_WEIGHT_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Font weight. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

## NODE_TEXT_LINE_COUNT

```c
NODE_TEXT_LINE_COUNT = 1031
```

Number of lines in the text. This attribute can be obtained as required through APIs.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 20


**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of lines in the text.|

## NODE_TEXT_OPTIMIZE_TRAILING_SPACE

```c
NODE_TEXT_OPTIMIZE_TRAILING_SPACE = 1032
```

Whether to optimize the trailing spaces at the end of each line during text layout. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to optimize the trailing spaces at the end of each line during text layout. The default value is **false**.<br>The value **true** means to optimize trailing spaces at the end of each line during text layout, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the trailing spaces at the end of each line are optimized during text layout.|

## NODE_TEXT_LINEAR_GRADIENT

```c
NODE_TEXT_LINEAR_GRADIENT = 1033
```

Linear gradient effect for text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient. The setting takes effect only when **direction** is set to **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is **180**.|
| .value[1].i32 | Direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection). When a direction other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** is set, the **angle** attribute is ignored. The default value is **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM**.|
| .value[2].i32 | Whether the colors are repeated. The value **false** means that the colors are not repeated, and **true** means the opposite. The default value is **false**.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| stops | Stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value.|
| size | Number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Values greater than the **colors** array length, values less than or equal to 0, or invalid values are not recommended.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient. The set value is used only when **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** is used. In other cases, the default value **0** is used.|
| .value[1].i32 | Direction of the linear gradient. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection).|
| .value[2].i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. The default value is **0**.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| stops | Stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.|
| size | Number of effective gradient colors.|

## NODE_TEXT_RADIAL_GRADIENT

```c
NODE_TEXT_RADIAL_GRADIENT = 1034
```

Radial gradient effect for text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the text box.|
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the text box. The coordinates of the upper left corner of the text box are [0, 0].|
| .value[2]?.f32 | Radius of the radial gradient. The default value is **0**.|
| .value[3]?.i32 | Whether the colors are repeated. The value **false** means that the colors are not repeated, and **true** means the opposite. The default value is **false**.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| stops | Stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value.|
| size | Number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Values greater than the **colors** array length, values less than or equal to 0, or invalid values are not recommended.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the text box.|
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the text box. The coordinates of the upper left corner of the text box are [0, 0].|
| .value[2]?.f32 | Radius of the radial gradient. The default value is **0**.|
| .value[3]?.i32 | Whether the colors are repeated. The value **0** means that the colors are not repeated, and **1** means the opposite. The default value is **0**.|
| .object | The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). It specifies an array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.|
| colors | Colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| stops | Stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.|
| size | Number of effective gradient colors.|

## NODE_TEXT_VERTICAL_ALIGN

```c
NODE_TEXT_VERTICAL_ALIGN = 1035
```

Vertical alignment mode of the text content. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the text content. The parameter type is [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment). The default value is **ARKUI_TEXT_VERTICAL_ALIGNMENT_BASELINE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the text content. The parameter type is [ArkUI_TextVerticalAlignment](capi-native-type-h.md#arkui_textverticalalignment).|

## NODE_TEXT_CONTENT_ALIGN

```c
NODE_TEXT_CONTENT_ALIGN = 1036
```

Vertical alignment mode of the text content area. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the text content area. The parameter type is [ArkUI_TextContentAlign](capi-native-type-h.md#arkui_textcontentalign). The default value is **ARKUI_TEXT_CONTENT_ALIGN_CENTER**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Vertical alignment mode of the text content area. The parameter type is [ArkUI_TextContentAlign](capi-native-type-h.md#arkui_textcontentalign).|

## NODE_TEXT_MIN_LINES

```c
NODE_TEXT_MIN_LINES = 1037
```

Minimum number of lines in the text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Minimum number of lines in the text.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Minimum number of lines in the text.|

## NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_ENABLE_SELECTED_DATA_DETECTOR = 1038
```

Whether to enable entity recognition for selected text.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable entity recognition for selected text. **true** to enable; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether entity recognition for selected text is enabled.|

## NODE_TEXT_MIN_LINE_HEIGHT

```c
NODE_TEXT_MIN_LINE_HEIGHT = 1040
```

Minimum line height. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Minimum line height of the text. The default value is **0**. The unit is fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum line height of the text. The unit is fp.|

## NODE_TEXT_MAX_LINE_HEIGHT

```c
NODE_TEXT_MAX_LINE_HEIGHT = 1041
```

Maximum line height. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Maximum line height. The default value is **0**, indicating that the maximum line height is not limited. The unit is fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Maximum line height of the text. The unit is fp.|

## NODE_TEXT_LINE_HEIGHT_MULTIPLE

```c
NODE_TEXT_LINE_HEIGHT_MULTIPLE = 1042
```

Multiple value of the multiple line height mode. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Multiple value of the multiple line height mode. The default value is **0**, indicating that the default line height is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Multiple value of the multiple line height mode.|

## NODE_TEXT_LAYOUT_MANAGER

```c
NODE_TEXT_LAYOUT_MANAGER = 1043
```

Text layout manager. This attribute can be obtained as required through APIs.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 22


**Returns**

| Type| Description|
| -- | -- |
| .object | Text layout manager object. The parameter type is [ArkUI_LayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md).|

## NODE_TEXT_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDIT_MENU_OPTIONS = 1044
```

Extended options of the text menu. This attribute can be set as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .object | Configuration data of the extended options of the text menu. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).|

## NODE_TEXT_BIND_SELECTION_MENU

```c
NODE_TEXT_BIND_SELECTION_MENU = 1045
```

Custom text selection menu. This attribute can be set as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .object | Configuration data of the custom text selection menu. The parameter type is [ArkUI_TextSelectionMenuOptions](capi-arkui-nativemodule-arkui-textselectionmenuoptions.md).|

## NODE_TEXT_TEXT_SELECTION

```c
NODE_TEXT_TEXT_SELECTION = 1046
```

Text selection area. After set, the selected area will be highlighted. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|
| .object | Selection options. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|
| .object | Selection options. The parameter type is [ArkUI_SelectionOptions](capi-arkui-nativemodule-arkui-selectionoptions.md).|

## NODE_TEXT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_COMPRESS_LEADING_PUNCTUATION = 1048
```

Whether to enable the feature of compressing punctuations at the beginning of a text line. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the feature of compressing punctuations at the beginning of a text line.<br>**true** to enable; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the feature of compressing punctuations is enabled at the beginning of a text line.|

## NODE_TEXT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INCLUDE_FONT_PADDING = 1049
```

Whether to add spacing to the first and last lines to avoid text truncation.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to add spacing to the first and last lines to avoid text truncation. **true** to add; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added to the first and last lines. **true** indicates spacing is added; **false** otherwise.|

## NODE_TEXT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_FALLBACK_LINE_SPACING = 1050
```

Whether the line height can be automatically adjusted based on the actual text height for multi-line text overlay. This enumerated value takes effect only when the line height is smaller than the actual text height.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **true** to be adjusted; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **true** means that the line height can be automatically adjusted; **false** otherwise.|

## NODE_TEXT_MARQUEE_OPTIONS

```c
NODE_TEXT_MARQUEE_OPTIONS = 1051
```

Configuration options of the text marquee mode. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Configuration options of the text marquee mode. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Configuration options of the text marquee mode. The parameter type is [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md).|

## NODE_TEXT_DIRECTION

```c
NODE_TEXT_DIRECTION = 1052
```

Text layout direction.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

## NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_SELECTED_DRAG_PREVIEW_STYLE = 1053
```

Drag preview style when the text is selected.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

## NODE_SPAN_CONTENT

```c
NODE_SPAN_CONTENT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SPAN = 2000
```

Text content attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Text content of the [span](arkui-ts/ts-basic-components-span.md).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Text content of the span.|

## NODE_SPAN_TEXT_BACKGROUND_STYLE

```c
NODE_SPAN_TEXT_BACKGROUND_STYLE = 2001
```

Text background style. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Text background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br>The second parameter is used to set the rounded corner of the text background. The options are as follows:<br>- .value[1].f32: radius of the four corners, in vp.<br>- .value[1].f32: radius of the upper left corner, in vp.|
| .value[2].f32 | Radius of the upper right corner, in vp.|
| .value[3].f32 | Radius of the lower left corner, in vp.|
| .value[4].f32 | Radius of the lower right corner, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Text background color, in 0xARGB format.|
| .value[1].f32 | Radius of the upper left corner, in vp.|
| .value[2].f32 | Radius of the upper right corner, in vp.|
| .value[3].f32 | Radius of the lower left corner, in vp.|
| .value[4].f32 | Radius of the lower right corner, in vp.|

## NODE_SPAN_BASELINE_OFFSET

```c
NODE_SPAN_BASELINE_OFFSET = 2002
```

Text baseline offset attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Baseline offset, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Baseline offset, in fp.|

## NODE_SPAN_FONT

```c
NODE_SPAN_FONT = 2003
```

Text style attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .string? | Font family. Use commas (,) to separate multiple fonts. This parameter is optional.|
| .value[0].f32 | Font size, in fp.|
| .value[1]?.i32 | Font weight. This parameter is optional. The value range is [100, 900]. The default value is **400**. A larger value indicates a bolder font.|
| .value[2]?.i32 | Font style. This parameter is optional. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle). The default value is **ARKUI_FONT_STYLE_NORMAL**.|
| ?.object | Font configurations. This parameter is optional. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Font family. Use commas (,) to separate multiple fonts.|
| .value[0].f32 | Font size, in fp.|
| .value[1].i32 | Font weight, without a unit. A larger value indicates a bolder font.|
| .value[2].i32 | Font style. The parameter type is [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle).|
| .object | Font configurations. The parameter type is [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md).|

## NODE_SPAN_FONT_WEIGHT

```c
NODE_SPAN_FONT_WEIGHT = 2004
```

Font weight attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Font weight. The value range is [100, 900]. The default value is **400**. A larger value indicates a bolder font.|
| ?.object | (Optional) font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Font weight, without a unit. A larger value indicates a bolder font.|
| .object | Font weight configurations. The parameter type is [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md).|

## NODE_IMAGE_SPAN_SRC

```c
NODE_IMAGE_SPAN_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_SPAN = 3000
```

Image source for an image span. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Image address of the image span.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Image address of the image span.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT

```c
NODE_IMAGE_SPAN_VERTICAL_ALIGNMENT = 3001
```

Alignment mode of the image with the text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode of the image with the text. The value is an enumerated value of [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode of the image with the text. The value is an enumerated value of [ArkUI_ImageSpanAlignment](capi-native-type-h.md#arkui_imagespanalignment).|

## NODE_IMAGE_SPAN_ALT

```c
NODE_IMAGE_SPAN_ALT = 3002
```

Placeholder image address for the image span. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Placeholder image address for the image span. GIF images are not supported.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Placeholder image address.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_IMAGE_SPAN_BASELINE_OFFSET

```c
NODE_IMAGE_SPAN_BASELINE_OFFSET = 3003
```

Baseline offset attribute of the **ImageSpan** component. This attribute can be set, reset, and obtained as required through APIs. A positive value means an upward offset, while a negative value means a downward offset. The default value is **0**, and the unit is fp.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Baseline offset, in fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Baseline offset, in fp.|

## NODE_IMAGE_SPAN_COLOR_FILTER

```c
NODE_IMAGE_SPAN_COLOR_FILTER = 3004
```

Color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 to .value[19].f32| Filter matrix array.|
| .size | Indicates that the size of the filter array is 5 x 4.|
| .object | Color filter pointer. The parameter type is [OH_Drawing_ColorFilter](../apis-arkgraphics2d/capi-drawing-oh-drawing-colorfilter.md).<br>Either **.object** or **.size** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 to .value[19].f32| Filter matrix array.|
| .size | Indicates that the size of the filter array is 5 x 4.|
| .object | Color filter pointer. The parameter type is [OH_Drawing_ColorFilter](../apis-arkgraphics2d/capi-drawing-oh-drawing-colorfilter.md).|

## NODE_IMAGE_SPAN_SUPPORT_SVG2

```c
NODE_IMAGE_SPAN_SUPPORT_SVG2 = 3005
```

Whether to enable the new SVG parsing capability, which allows you to set the scope of SVG parsing functionality support. This attribute can be set, reset, and obtained as required through APIs. After the **ImageSpan** component is created, the value of this attribute cannot be dynamically changed.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the new SVG parsing capability. **true**: enable enhanced SVG tag parsing. **false**: use original SVG tag parsing.<br>The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the new SVG parsing capability is enabled.|
