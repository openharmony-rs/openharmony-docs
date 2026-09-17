# Datepicker

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_DATE_PICKER_LUNAR

```c
NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER
```

**Description**

Defines whether to display the lunar calendar in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to display the lunar calendar in the date picker. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to display the lunar calendar in the date picker.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_START

```c
NODE_DATE_PICKER_START
```

**Description**

Defines the start date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: date. The default value is <b>"1970-1-1"</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: date.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_END

```c
NODE_DATE_PICKER_END
```

**Description**

Defines the end date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: date. The default value is <b>"2100-12-31"</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: date.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_SELECTED

```c
NODE_DATE_PICKER_SELECTED
```

**Description**

Defines the selected date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: date. The default value is <b>"2024-01-22"</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: date.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight for the top and bottom items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_TEXT_STYLE

```c
NODE_DATE_PICKER_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight of all items except the top, bottom, and selected items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_SELECTED_TEXT_STYLE

```c
NODE_DATE_PICKER_SELECTED_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight of the selected item in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_MODE

```c
NODE_DATE_PICKER_MODE = 13007
```

**Description**

Defines the mode of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>value[0].i32: the mode. The value is and enum of {@link ArkUI_DatePickerMode}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>value[0].i32: the mode. The value is and enum of {@link ArkUI_DatePickerMode}.</li> </ul>

**Since**: 18

### NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008
```

**Description**

Defines whether haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and<br><b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].i32: whether to feedback.</li> </ul>

**Since**: 18

### NODE_DATE_PICKER_CAN_LOOP

```c
NODE_DATE_PICKER_CAN_LOOP = 13009
```

**Description**

Defines whether to support scroll looping for the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to support scroll looping. The value <b>true</b> means to support scroll looping, and<br><b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>value[0].i32: The value <b>1</b> means to support scroll looping, and <b>0</b> means the opposite.</li> </ul>

**Since**: 20


