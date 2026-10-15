# Timepicker

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TIME_PICKER_SELECTED

```c
NODE_TIME_PICKER_SELECTED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER
```

**Description**

Defines the time of the selected item. in the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: time. The default value is the current system time.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: time.</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_USE_MILITARY_TIME

```c
NODE_TIME_PICKER_USE_MILITARY_TIME
```

**Description**

Whether the display time of the time picker is in 24-hour format. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the display time is in 24-hour format. The default value is <b>0</b>. <b>1</b>: The display time is in 24-hour format. <b>0</b>: The display time is in 12-hour format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the display time is in 24-hour format. The value <b>1</b> indicates that the time is displayed in the 24-hour format (corresponding to <b>true</b>), and <b>0</b> indicates that the time is displayed in the 12-hour format (corresponding to <b>false</b>).</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE
```

**Description**

Text style for edge items (the second item above or below the selected item). This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_TEXT_STYLE

```c
NODE_TIME_PICKER_TEXT_STYLE
```

**Description**

Text color, font size, and font weight for all items except edge items and selected items in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TIME_PICKER_SELECTED_TEXT_STYLE
```

**Description**

Text color, font size, and font weight of the selected item in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>. When not set, the system default style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: five parameters of the string type, separated by semicolons (;):<br> Parameter 1: text color, in #ARGB format.<br> Parameter 2: font size, in fp. The value is a number.<br> Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").<br> Parameter 4: fonts, separated by commas (,).<br> Parameter 5: font style. Available options are ("normal", "italic").<br> Example: <b>"#ff182431;14;normal;Arial,HarmonyOS Sans;normal"</b>.</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_START

```c
NODE_TIME_PICKER_START = 14005
```

**Description**

Start time of the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: time. The default value is <b>"0:0"</b>. When set, only hours and minutes are supported, separated by <b>:</b> or <b>-</b> (for example, 12:59 or 12-59).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: start time to set. Format: hour:minute:second (for example, 0:0:0).</li> </ul>

**Since**: 18

### NODE_TIME_PICKER_END

```c
NODE_TIME_PICKER_END = 14006
```

**Description**

End time of the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: time. The default value is <b>"23:59"</b>. When set, only hours and minutes are supported, separated by <b>:</b> or <b>-</b> (for example, 23:59 or 23-59).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: end time to set. Format: hour:minute:second (for example, 23:59:0).</li> </ul>

**Since**: 18

### NODE_TIME_PICKER_ENABLE_CASCADE

```c
NODE_TIME_PICKER_ENABLE_CASCADE = 14007
```

**Description**

Whether the AM/PM indicator automatically switches based on the hour in 12-hour format. This attribute can be set, reset, and obtained as required through APIs. In the 24-hour format, this attribute does not take effect.<br> Use scenario: It is suitable for scenarios that require a friendly 12-hour format selection experience. For example, when the user scrolls to select the hour, the AM/PM indicator changes automatically without manual switching.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the AM/PM indicator automatically switches based on the hour in 12-hour format. The default value is <b>0</b>. The value <b>1</b> means that the AM/PM indicator automatically switches based on the hour in 12-hour format, and <b>0</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the AM/PM indicator automatically switches based on the hour in 12-hour format. The value <b>1</b> means that the AM/PM indicator automatically switches (corresponding to <b>true</b>), and the value <b>0</b> that the AM/PM indicator does not automatically switch (corresponding to <b>false</b>).</li> </ul>

**Since**: 18


