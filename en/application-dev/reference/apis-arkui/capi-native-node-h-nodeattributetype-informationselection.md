# ArkUI_NodeAttributeType (Information Selection Component Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for information selection components including **DatePicker**, **TimePicker**, **TextPicker**, and **CalendarPicker**.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)


## NODE_DATE_PICKER_LUNAR

```c
NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER = 13000
```

Whether to display the lunar calendar in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to display the lunar calendar. The default value is **false**. **true** to display; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the lunar calendar is displayed.|

## NODE_DATE_PICKER_START

```c
NODE_DATE_PICKER_START = 13001
```

Start date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Date. The default value is **"1970-1-1"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Date.|

## NODE_DATE_PICKER_END

```c
NODE_DATE_PICKER_END = 13002
```

End date of the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Date. The default value is **"2100-12-31"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Date.|

## NODE_DATE_PICKER_SELECTED

```c
NODE_DATE_PICKER_SELECTED = 13003
```

Date of the selected item in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Date. The default value is **"2024-01-22"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Date.|

## NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE = 13004
```

Text color, font size, and font weight for the top and bottom items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_DATE_PICKER_TEXT_STYLE

```c
NODE_DATE_PICKER_TEXT_STYLE = 13005
```

Text color, font size, and font weight for all items except edge items and selected items in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_DATE_PICKER_SELECTED_TEXT_STYLE

```c
NODE_DATE_PICKER_SELECTED_TEXT_STYLE = 13006
```

Text color, font size, and font weight of the selected item in the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_DATE_PICKER_MODE

```c
NODE_DATE_PICKER_MODE = 13007
```

Date column to be displayed. This attribute can be set, reset, and obtained as required through APIs. **DatePicker** displays different styles of date columns.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Type of the date column to be displayed. The parameter type is [ArkUI_DatePickerMode](capi-picker-h.md#arkui_datepickermode).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the date column to be displayed. The parameter type is [ArkUI_DatePickerMode](capi-picker-h.md#arkui_datepickermode).|

## NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008
```

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Whether to enable haptic feedback. **true** to enable; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Whether haptic feedback is enabled.|

## NODE_DATE_PICKER_CAN_LOOP

```c
NODE_DATE_PICKER_CAN_LOOP = 13009
```

Whether to enable looping for the date picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable looping. **true** to enable; **false** otherwise. The default value is **true**. If an invalid value is provided, the default value is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether looping is enabled. The value **1** means that the looping is enabled, and **0** means the opposite.<br>Note: When looping is enabled, the year increments or decrements in linkage with the month's cycle, and the month increments or decrements in linkage with the day's cycle.<br>When looping is disabled, scrolling beyond the bounds of the year, month, or day columns is prevented, and cross-column value synchronization (between year, month, and day) is also disabled.|

## NODE_TIME_PICKER_SELECTED

```c
NODE_TIME_PICKER_SELECTED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER = 14000
```

Time of the selected item in the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Time. The default value is current system time. Format: only hours and minutes are supported (for example, 23:59/23-59).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Time. The default value is current system time. Format: hour, minute, and second (for example, 23,59,1).|

## NODE_TIME_PICKER_USE_MILITARY_TIME

```c
NODE_TIME_PICKER_USE_MILITARY_TIME = 14001
```

Whether the display time of the time picker is in 24-hour format. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the display time is in 24-hour format. The default value is **false**. **true**: The display time is in 24-hour format. **false**: The display time is in 12-hour format.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the display time is in 24-hour format.|

## NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE = 14002
```

Text style for edge items (the second item above or below the selected item). This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_TIME_PICKER_TEXT_STYLE

```c
NODE_TIME_PICKER_TEXT_STYLE = 14003
```

Text color, font size, and font weight for all items except edge items and selected items in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_TIME_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TIME_PICKER_SELECTED_TEXT_STYLE = 14004
```

Text color, font size, and font weight of the selected item in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_TIME_PICKER_START

```c
NODE_TIME_PICKER_START = 14005
```

Start time of the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .string | Time. The default value is **"0:0:0"**. Format: only hours and minutes are supported (for example, 12:59/12-59).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Time. The default value is **"0:0:0"**. Format: hour, minute, and second (for example, 12:59:0).|

## NODE_TIME_PICKER_END

```c
NODE_TIME_PICKER_END = 14006
```

End time of the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .string | Time. The default value is **"23:59:59"**. Format: only hours and minutes are supported (for example, 23:59/23-59).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Time. The default value is **"23:59:59"**. Format: hour, minute, and second (for example, 23:59:0).|

## NODE_TIME_PICKER_ENABLE_CASCADE

```c
NODE_TIME_PICKER_ENABLE_CASCADE = 14007
```

Whether the AM/PM indicator automatically switches based on the hour in 12-hour format. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the AM/PM indicator automatically switches based on the hour in 12-hour format. The default value is **false**. **true** means that the AM/PM indicator automatically switches based on the hour in 12-hour format, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the AM/PM indicator automatically switches based on the hour in 12-hour format.|

## NODE_TEXT_PICKER_OPTION_RANGE

```c
NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER = 15000
```

Data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Type of the text picker, specified using [ArkUI_TextPickerRangeType](capi-picker-h.md#arkui_textpickerrangetype). The default value is **ARKUI_TEXTPICKER_RANGETYPE_SINGLE**.|
| ?.string | string input, whose format varies by picker type.<br>1: single-column picker. The input format is a group of strings separated by semicolons (;).<br>2: multi-column picker. Multiple pairs of plain text strings are supported. The pairs are separated by semicolons (;), and strings within each pair are separated by commas (,).|
| ?.object | object input, whose format varies by picker type.<br>1: single-column picker with image support. The input struct is [ARKUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md).<br>2: multi-column cascading picker. The input struct is [ARKUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the text picker, specified using [ArkUI_TextPickerRangeType](capi-picker-h.md#arkui_textpickerrangetype).|
| ?.string | string output, whose format varies by picker type.<br>1: single-column picker. The output format is a group of strings separated by semicolons (;).<br>2: multi-column picker. Multiple pairs of plain text strings are output. The pairs are separated by semicolons (;), and strings within each pair are separated by commas (,).|

## NODE_TEXT_PICKER_OPTION_SELECTED

```c
NODE_TEXT_PICKER_OPTION_SELECTED = 15001
```

Index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Index. If there are multiple index values, add them one by one.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Index. If there are multiple index values, add them one by one.|

## NODE_TEXT_PICKER_OPTION_VALUE

```c
NODE_TEXT_PICKER_OPTION_VALUE = 15002
```

Value of the default selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Value of the selected item. If there are multiple values, add them one by one and separate them with semicolons (;).|

**Returns**

| Type| Description|
| -- | -- |
| .string | Value of the selected item. If there are multiple values, add them one by one and separate them with semicolons (;).|

## NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE = 15003
```

Text color, font size, and font weight for the top and bottom items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_TEXT_PICKER_TEXT_STYLE

```c
NODE_TEXT_PICKER_TEXT_STYLE = 15004
```

Text color, font size, and font weight for all items except the top, bottom, and selected items in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_TEXT_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TEXT_PICKER_SELECTED_TEXT_STYLE = 15005
```

Text color, font size, and font weight of the selected item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Five parameters of the string type, separated by semicolons (;).<br>Parameter 1: text color, in #ARGB format.<br>Parameter 2: font size, in fp. The value is a number.<br>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br>Parameter 4: fonts, separated by commas (,).<br>Parameter 5: font style. Available options are ("normal", "italic").<br>Example: **"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"**.|

## NODE_TEXT_PICKER_SELECTED_INDEX

```c
NODE_TEXT_PICKER_SELECTED_INDEX = 15006
```

Index of the default selected item in the data selection range of the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0...].i32 | Array of the indexes of the default items in the data selection range.|

## NODE_TEXT_PICKER_CAN_LOOP

```c
NODE_TEXT_PICKER_CAN_LOOP = 15007
```

Whether to enable looping for the picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable looping. **true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether looping is enabled. The value **1** means that the looping is enabled, and **0** means the opposite.|

## NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT

```c
NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT = 15008
```

Height of each item in the text picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Item height, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Item height, in vp.|

## NODE_TEXT_PICKER_COLUMN_WIDTHS

```c
NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009
```

Width of each column in the picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the first column, specified as a percentage of the total width. By default, all columns have equal widths.|
| .value[1]?.f32 | Width of the second column, specified as a percentage of the total width. By default, all columns have equal widths.|
| .value[2]?.f32 | Width of the third column, specified as a percentage of the total width. By default, all columns have equal widths.<br>...|
| .value[n]?.f32 | Width of the (n+1)-th column, specified as a percentage of the total width. By default, all columns have equal widths.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the first column, specified as a percentage of the total width.|
| .value[1].f32 | Width of the second column, specified as a percentage of the total width.|
| .value[2].f32 | Width of the third column, specified as a percentage of the total width.<br>...|
| .value[n].f32 | Width of the (n+1)-th column, specified as a percentage of the total width.|

## NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010
```

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Whether to enable haptic feedback. **true** to enable; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Whether haptic feedback is enabled.|

## NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE

```c
NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011
```

Background color and border radius of the selected item. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format, for example, **0xFF1122FF**.|
| .value[1].f32 | Unified radius for all four corners, in vp.|
| .value[1].f32 | Radius of the upper left corner, in vp.|
| .value[2].f32 | Radius of the upper right corner, in vp.|
| .value[3].f32 | Radius of the lower left corner, in vp.|
| .value[4].f32 | Radius of the lower right corner, in vp.<br>Default values: background color = 0x0C182431; border radius = 24.0.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format, for example, **0xFF1122FF**.|
| .value[1].f32 | Radius of the upper left corner, in vp.|
| .value[2].f32 | Radius of the upper right corner, in vp.|
| .value[3].f32 | Radius of the lower left corner, in vp.|
| .value[4].f32 | Radius of the lower right corner, in vp.|

## NODE_PICKER_OPTION_SELECTED_INDEX

```c
NODE_PICKER_OPTION_SELECTED_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER
```

Index of the default selected item in the picker's selection range. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Index value. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Index value.|

## NODE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_PICKER_ENABLE_HAPTIC_FEEDBACK = 1018001
```

Whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable haptic feedback. **true** to enable; **false** otherwise. The default value is **true**. After this feature is enabled, whether haptic feedback is available depends on the hardware support of the system.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether haptic feedback is enabled.|

## NODE_PICKER_CAN_LOOP

```c
NODE_PICKER_CAN_LOOP = 1018002
```

Whether the picker supports looping. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the picker supports looping. **true** to support; **false** otherwise. The default value is **true**.<br>If the number of child components is less than 8, looping will not occur regardless of whether the value is **true** or **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the picker supports looping. **true** indicates that scrolling is supported; **false** indicates that scrolling is not supported.|

## NODE_PICKER_SELECTION_INDICATOR

```c
NODE_PICKER_SELECTION_INDICATOR = 1018003
```

Picker indicator style. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Picker indicator style. The parameter type is [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Picker indicator style. The parameter type is [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).|

## NODE_PICKER_DISPLAYED_ITEM_COUNT

```c
NODE_PICKER_DISPLAYED_ITEM_COUNT = 1018004
```

Number of displayed items in the **Picker** container. The semantics is the same as that of [displayedItemCount](arkui-ts/ts-container-ui-picker-component.md#displayeditemcount) in [UIPickerComponent](arkui-ts/ts-container-ui-picker-component.md) on the ArkTS side. If this attribute is not set, the value **7** is used. When **Picker** is in a three-dimensional wheel style, all items except the selected ones rotate at an angle, and the actual visible height is less than the item line height. To increase the number of visible lines or the line height, increase the container height accordingly. For details, see [UIPickerComponent](arkui-ts/ts-container-ui-picker-component.md). This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of displayed items. The value is an integer within the range of [2, 9]. If a number with a decimal is passed, it is rounded down. If an even number is passed, it is rounded up to the nearest odd number (for example, 2 becomes 3 and 8 becomes 9). If a number is not within the range, the default value **7** is used.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of displayed items.|

## NODE_PICKER_ITEM_HEIGHT

```c
NODE_PICKER_ITEM_HEIGHT = 1018005
```

Height of each item in the **Picker** container. The semantics is the same as that of [itemHeight](arkui-ts/ts-container-ui-picker-component.md#itemheight) in [UIPickerComponent](arkui-ts/ts-container-ui-picker-component.md) on the ArkTS side. If this attribute is not set, the height of each item is 40 vp. C APIs pass the height value in vp. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Item height, in vp. The valid range is [40, 64]. If the value is less than 40 vp or greater than 64 vp, the default value **40** vp is used. The value cannot be in percentage.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Item height, in vp.|

## NODE_CALENDAR_PICKER_HINT_RADIUS

```c
NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER = 16000
```

Corner radius of the background of the selected state in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Corner radius of the background of the selected state in the calendar picker. The default value is **16.0**, in vp, which indicates that the background is a circle. If the value is **0.0**, the background is a right-angled rectangle. If the value is within the (0.0, 16.0) range, the background is a rounded rectangle. If the value is a negative number or greater than **16.0**, the default value **16.0** is used, which means the background is a circle.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Corner radius of the background of the selected state in the calendar picker. The default value is **16.0**, in vp, which indicates that the background is a circle. The value range is [0.0, 16.0]. If the value is **0.0**, the background is a right-angled rectangle.|

## NODE_CALENDAR_PICKER_SELECTED_DATE

```c
NODE_CALENDAR_PICKER_SELECTED_DATE = 16001
```

Date of the selected item in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Selected year.|
| .value[1].u32 | Selected month.|
| .value[2].u32 | Selected day.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Selected year.|
| .value[1].u32 | Selected month.|
| .value[2].u32 | Selected day.|

## NODE_CALENDAR_PICKER_EDGE_ALIGNMENT

```c
NODE_CALENDAR_PICKER_EDGE_ALIGNMENT = 16002
```

How the calendar picker is aligned with the entry component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-picker-h.md#arkui_calendaralignment).|
| .value[1]?.f32 | Offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode.|
| .value[2]?.f32 | Offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-picker-h.md#arkui_calendaralignment).|
| .value[1].f32 | Offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode.|
| .value[2].f32 | Offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode.|

## NODE_CALENDAR_PICKER_TEXT_STYLE

```c
NODE_CALENDAR_PICKER_TEXT_STYLE = 16003
```

Text color, font size, and font weight in the entry area of the calendar picker.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.u32 | Text color of the entry area.|
| .value[1]?.f32 | Font size of the entry area, in fp.|
| .value[2]?.i32 | Font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Text color of the entry area.|
| .value[1].f32 | Font size of the entry area, in fp.|
| .value[2].i32 | Font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight).|

## NODE_CALENDAR_PICKER_START

```c
NODE_CALENDAR_PICKER_START = 16004
```

Start date of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .string | Date. The value format is "YYYY-M-D", for example, **"1970-1-1"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Date.|

## NODE_CALENDAR_PICKER_END

```c
NODE_CALENDAR_PICKER_END = 16005
```

End date of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .string | Date. The value format is "YYYY-MM-DD", for example, **"2100-12-31"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Date.|

## NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE

```c
NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006
```

Disabled date ranges of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| .string | String representing the disabled date ranges. The format is "start_date,end_date" for each range, with multiple ranges separated by commas (,).<br>Example: **"1910-01-01,1910-12-31,2020-01-01,2020-12-31"**.|

**Returns**

| Type| Description|
| -- | -- |
| .string | String representing the disabled date ranges.|

## NODE_CALENDAR_PICKER_MARK_TODAY

```c
NODE_CALENDAR_PICKER_MARK_TODAY = 16007
```

Whether to highlight the current system date in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 19


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to highlight the current system date in the calendar picker. The default value is **false**. **true** to highlight; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the current system date is highlighted in the calendar picker.|

<!--no_check-->