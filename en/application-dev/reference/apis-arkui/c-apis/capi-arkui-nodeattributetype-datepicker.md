# Datepicker

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_DATE_PICKER_LUNAR

```c
NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER
```

**Description**

Defines whether to display the lunar calendar in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to display the lunar calendar in the date picker. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to display the lunar calendar in the date picker.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_START

```c
NODE_DATE_PICKER_START
```

**Description**

Start date of the date picker. This attribute can be set, reset, and obtained as required through APIs. The start date limits the valid range of date selection, and a selected date out of range is automatically adjusted.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The default value is <b>"1970-1-1"</b>. Format: <i>YYYY-MM-DD</i>, where <b>YYYY</b> supports 1 or 4 digits, and <b>MM</b> and <b>DD</b> are 1-2 digit numbers.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: start date to set, in the format of <i>YYYY-MM-DD</i>.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_END

```c
NODE_DATE_PICKER_END
```

**Description**

End date of the date picker. This attribute can be set, reset, and obtained as required through APIs. The end date limits the valid range of date selection, and a selected date out of range is automatically adjusted.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The default value is <b>"2100-12-31"</b>. Format: <i>YYYY-MM-DD</i>, where <b>YYYY</b> supports 1 or 4 digits, and <b>MM</b> and <b>DD</b> are 1-2 digit numbers.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: end date to set, in the format of <i>YYYY-MM-DD</i>.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_SELECTED

```c
NODE_DATE_PICKER_SELECTED
```

**Description**

Date of the selected item in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The default value is <b>"2024-01-22"</b>. When not set, the default value is used. Format: <i>YYYY-MM-DD</i>, where <b>YYYY</b> supports 1 or 4 digits, and <b>MM</b> and <b>DD</b> are 1-2 digit numbers.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: selected date, in the format of <i>YYYY-MM-DD</i>.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE
```

**Description**

Text color, font size, and font weight for the top and bottom items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_TEXT_STYLE

```c
NODE_DATE_PICKER_TEXT_STYLE
```

**Description**

Text color, font size, and font weight for all items except edge items and selected items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_SELECTED_TEXT_STYLE

```c
NODE_DATE_PICKER_SELECTED_TEXT_STYLE
```

**Description**

Text color, font size, and font weight of the selected item in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_DATE_PICKER_MODE

```c
NODE_DATE_PICKER_MODE = 13007
```

**Description**

Date column to be displayed. <b>DatePicker</b> displays different styles of date columns. This attribute can be set, reset, and obtained as required through APIs.<br> Use scenario: Select an appropriate date display mode based on application requirements. For example, use the year/month/day mode when precise selection down to the day is required, and use the year/month mode when only the month is required.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: type of the date column to be displayed. The parameter type is [ArkUI_DatePickerMode](capi-picker-h.md#arkui_datepickermode). Default value: the complete date columns (year, month, day).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: type of the date column to be displayed. The parameter type is [ArkUI_DatePickerMode](capi-picker-h.md#arkui_datepickermode).</li> </ul>

**Since**: 18

### NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008
```

**Description**

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable haptic feedback. The value <b>1</b> indicates to enable, and <b>0</b> indicates the opposite. After enabled, whether haptic feedback exists depends on the hardware support of the system.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether haptic feedback is enabled. The value <b>1</b> indicates haptic feedback is enabled, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 18

### NODE_DATE_PICKER_CAN_LOOP

```c
NODE_DATE_PICKER_CAN_LOOP = 13009
```

**Description**

Whether to enable looping for the date picker. This attribute can be set, reset, and obtained as required through APIs.<br> Use scenario: Looping is suitable for scenarios with limited options where a quick selection experience is desired (such as month selection); non-looping is suitable for scenarios where options have clear boundaries and the user selection range needs to be restricted (such as date selection to avoid confusion across years).<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable looping. <b>1</b> to enable; <b>0</b> otherwise. The default value is <b>1</b>. If an invalid value is provided, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether looping is enabled. The value <b>1</b> means that the looping is enabled, and <b>0</b> means the opposite.<br> Note: When looping is enabled, the year increments or decrements in linkage with the month's cycle, and the month increments or decrements in linkage with the day's cycle.<br> When looping is disabled, scrolling beyond the bounds of the year, month, or day columns is prevented, and cross-column value synchronization (between year, month, and day) is also disabled.</li> </ul>

**Since**: 20


