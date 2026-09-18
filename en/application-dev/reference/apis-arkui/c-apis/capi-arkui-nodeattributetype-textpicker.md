# Textpicker

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_PICKER_OPTION_RANGE

```c
NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER
```

**Description**

Defines the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: type of the text picker {@link ArkUI_TextPickerRangeType}.<br>The default value is <b>ARKUI_TEXTPICKER_RANGETYPE_SINGLE</b>. </li><br><li>.string: string input, whose format varies by picker type.</li><br><li>1: single-column picker. The input format is a group of strings separated by semicolons (;).</li><br><li>2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by<br>semicolons (;), and strings within each pair are separated by commas (,).</li><br><li>.object: Object input, whose format varies by picker type.</li><br><li>1: single-column picker with image support. The input structure is {@link ARKUI_TextPickerRangeContent}.</li><br><li>2: multi-column interconnected picker. The input structure is {@link ARKUI_TextPickerCascadeRangeContent}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: type of the text picker {@link ArkUI_TextPickerRangeType}.</li><br><li>.string: string output, whose format varies by picker type.</li><br><li>1: single-column picker. The output format is a group of strings separated by semicolons (;).</li><br><li>2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by<br>semicolons (;), and strings within each pair are separated by commas (,).</li><br><li>.string: Object output, whose format varies by picker type.</li><br><li>1: single-column picker with image support. The output structure is {@link ARKUI_TextPickerRangeContent}.</li><br><li>2: multi-column interconnected picker. The output structure is {@link ARKUI_TextPickerCascadeRangeContent}.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_OPTION_SELECTED

```c
NODE_TEXT_PICKER_OPTION_SELECTED
```

**Description**

Defines the index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: index. If there are multiple index values, add them one by one.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: index. If there are multiple index values, add them one by one.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_OPTION_VALUE

```c
NODE_TEXT_PICKER_OPTION_VALUE
```

**Description**

Defines the value of the default selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: value of the selected item. If there are multiple values, add them one by one and<br>separate them with semicolons (;).</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: value of the selected item. If there are multiple values, add them one by one and separate them with semicolons (;).</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight for the top and bottom items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_TEXT_STYLE

```c
NODE_TEXT_PICKER_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight for all items except the top, bottom, and selected items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TEXT_PICKER_SELECTED_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight for the selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_SELECTED_INDEX

```c
NODE_TEXT_PICKER_SELECTED_INDEX
```

**Description**

Defines the index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul> <li>.value[0...].i32: index of the default item in the data selection range.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_CAN_LOOP

```c
NODE_TEXT_PICKER_CAN_LOOP
```

**Description**

Defines whether to support scroll looping for the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to support scroll looping. The value <b>true</b> means to support scroll looping, and<br><b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].i32: The value <b>1</b> means to support scroll looping, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT

```c
NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT
```

**Description**

Defines the height of each item in the picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: item height, in vp.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].f32: item height, in vp.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010
```

**Description**

Defines whether haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<br><b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].i32: whether to feedback.</li> </ul>

**Since**: 18

### NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE

```c
NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011
```

**Description**

Defines the background color and border radius of the selected items. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br><li>1: .value[1].f32: radius of the four corners.</li><br><li>2: .value[1].f32: radius of the upper left corner.</li><br><li>.value[2].f32: radius of the upper right corner.</li><br><li>.value[3].f32: radius of the lower left corner.</li><br><li>.value[4].f32: radius of the lower right corner.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br><li>.value[1].f32: radius of the upper left corner.</li><br><li>.value[2].f32: radius of the upper right corner.</li><br><li>.value[3].f32: radius of the lower left corner.</li><br><li>.value[4].f32: radius of the lower right corner.</li> </ul>

**Since**: 20

### NODE_TEXT_PICKER_COLUMN_WIDTHS

```c
NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009
```

**Description**

Defines the column width of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: percentage of total width. The default value is that all colulmns are equal width.</li><br><li>.value[1]?.f32: percentage of total width. The default value is that all colulmns are equal width.</li><br><li>.value[2]?.f32: percentage of total width. The default value is that all colulmns are equal width.</li><br><li>...</li><br><li>.value[n]?.f32: percentage of total width. The default value is that all colulmns are equal width.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].f32: percentage of total width.</li><br><li>value[1].f32: percentage of total width.</li><br><li>value[2].f32: percentage of total width.</li><br><li>...</li><br><li>value[n].f32: percentage of total width.</li> </ul>

**Since**: 18


