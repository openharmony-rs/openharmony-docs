# Textpicker

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_PICKER_OPTION_RANGE

```c
NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER
```

**Description**

Defines the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: type of the text picker [ArkUI_TextPickerRangeType](capi-picker-h.md#arkui_textpickerrangetype). The default value is <b>ARKUI_TEXTPICKER_RANGETYPE_SINGLE</b>. </li> <li>.string: string input, whose format varies by picker type.</li> <li>1: single-column picker. The input format is a group of strings separated by semicolons (;).</li> <li>2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by semicolons (;), and strings within each pair are separated by commas (,).</li> <li>.object: Object input, whose format varies by picker type.</li> <li>1: single-column picker with image support. The input structure is [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md).</li> <li>2: multi-column interconnected picker. The input structure is [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: type of the text picker [ArkUI_TextPickerRangeType](capi-picker-h.md#arkui_textpickerrangetype).</li> <li>.string: string output, whose format varies by picker type.</li> <li>1: single-column picker. The output format is a group of strings separated by semicolons (;).</li> <li>2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by semicolons (;), and strings within each pair are separated by commas (,).</li> <li>.string: Object output, whose format varies by picker type.</li> <li>1: single-column picker with image support. The output structure is [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md).</li> <li>2: multi-column interconnected picker. The output structure is [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md).</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_OPTION_SELECTED

```c
NODE_TEXT_PICKER_OPTION_SELECTED
```

**Description**

Index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs. This attribute can be used only after the option list is set through [NODE_TEXT_PICKER_OPTION_RANGE](capi-native-node-h.md#arkui_nodeattributetype).<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: index of the default selected item in the picker option array. The value range is [0, length - 1]. An exception is thrown if the value is out of range. For a multi-column picker, if multiple index values exist, add them one by one. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: index of the selected item in the picker option array. If multiple indexes exist, add them one by one.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_OPTION_VALUE

```c
NODE_TEXT_PICKER_OPTION_VALUE
```

**Description**

Value of the default selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: value of the selected item. If multiple values exist, add them one by one, separated by semicolons (;). Default value: empty string. When not set, use the default value.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: value of the selected item. If there are multiple values, add them one by one and separate them with semicolons (;).</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE
```

**Description**

Text color, font size, and font weight for the top and bottom items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_TEXT_STYLE

```c
NODE_TEXT_PICKER_TEXT_STYLE
```

**Description**

Text color, font size, and font weight for all items except the top, bottom, and selected items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TEXT_PICKER_SELECTED_TEXT_STYLE
```

**Description**

Text color, font size, and font weight of the selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_SELECTED_INDEX

```c
NODE_TEXT_PICKER_SELECTED_INDEX
```

**Description**

Index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs. This attribute can be used only after the option list is set through [NODE_TEXT_PICKER_OPTION_RANGE](capi-native-node-h.md#arkui_nodeattributetype). After the option list is set, if the index array is not set through this attribute, the first item of each column is selected by default.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0...].i32: array of the indexes of the default selected items in the picker option array. When used for a multi-column picker, it indicates the index of the default selected item in each column. Default value: <b>0</b> for each column. Value range: the index of each column is in [0, length of the corresponding column - 1]. An exception is thrown when the value is out of range.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0...].i32: array of the indexes of the currently selected items. When used for a multi-column picker, it indicates the index of the selected item in each column.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_CAN_LOOP

```c
NODE_TEXT_PICKER_CAN_LOOP
```

**Description**

Whether to enable looping for the picker. This attribute can be set, reset, and obtained as required through APIs.<br> Use scenario: Looping is suitable for scenarios with limited options where a quick selection experience is desired (such as province selection). Non-looping is suitable for scenarios where options have clear boundaries and the user selection range needs to be restricted (such as quantity selection to avoid misoperation).<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable looping. <b>1</b> to enable; <b>0</b> otherwise. Default value: <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether looping is enabled. The value <b>1</b> means that the looping is enabled, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT

```c
NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT
```

**Description**

Height of each item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: height of the currently set item, in vp. Default value: <b>40.0vp</b>. When not set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: height of the currently set item, in vp.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010
```

**Description**

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable haptic feedback. The value <b>1</b> indicates to enable, and <b>0</b> indicates the opposite. When enabled, whether haptic feedback exists depends on the hardware support of the system.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether haptic feedback is enabled. The value <b>1</b> indicates haptic feedback is enabled, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 18

### NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE

```c
NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011
```

**Description**

Background color and border radius of the selected item. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format. <b>A</b> indicates the opacity (0x00 fully transparent to 0xFF fully opaque), and <b>RGB</b> indicates the color value (0x000000 to 0xFFFFFF). Each byte ranges from 0x00 to 0xFF. For example, <b>0xFF1122FF</b> indicates a fully opaque blue.</li> <li>.value[1].f32: radius of the upper left corner, in vp.</li> <li>.value[2].f32: radius of the upper right corner, in vp.</li> <li>.value[3].f32: radius of the lower left corner, in vp.</li> <li>.value[4].f32: radius of the lower right corner, in vp.<br> Default background color: 0x0C182431; default corner radius: 24.0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <li>.value[1].f32: radius of the upper left corner, in vp.</li> <li>.value[2].f32: radius of the upper right corner, in vp.</li> <li>.value[3].f32: radius of the lower left corner, in vp.</li> <li>.value[4].f32: radius of the lower right corner, in vp.</li> </ul>

**Since**: 20

### NODE_TEXT_PICKER_COLUMN_WIDTHS

```c
NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009
```

**Description**

Width of each column in the picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: width of the first column, specified as a percentage of the total width. By default, all columns have equal widths. When not set, the columns are evenly divided.</li> <li>.value[1]?.f32: width of the second column, specified as a percentage of the total width. By default, all columns have equal widths.</li> <li>.value[2]?.f32: width of the third column, specified as a percentage of the total width. By default, all columns have equal widths.</li> <li>...</li> <li>.value[n]?.f32: width of the (n+1)-th column, specified as a percentage of the total width. By default, all columns have equal widths.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: width of the first column, specified as a percentage of the total width.</li> <li>.value[1].f32: width of the second column, specified as a percentage of the total width.</li> <li>.value[2].f32: width of the third column, as a percentage of the total width.</li> <li>...</li> <li>.value[n].f32: width of the (n+1)-th column, specified as a percentage of the total width.</li> </ul>

**Since**: 18


