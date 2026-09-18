# Timepicker

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TIME_PICKER_SELECTED

```c
NODE_TIME_PICKER_SELECTED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER
```

**Description**

Defines the time of the selected item. in the timer picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: time. The default value is the current system time.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: time.</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_USE_MILITARY_TIME

```c
NODE_TIME_PICKER_USE_MILITARY_TIME
```

**Description**

Defines whether the display time is in 24-hour format. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the display time is in 24-hour format. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the display time is in 24-hour format.</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight for the top and bottom items in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_TEXT_STYLE

```c
NODE_TIME_PICKER_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight of all items except the top, bottom, and selected items in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TIME_PICKER_SELECTED_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight of the selected item in the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: array of five parameters of the string type, separated by semicolons (;).</li><br><li>Parameter 1: font color, in #ARGB format.</li><br><li>Parameter 2: font size, in fp. The value is a number.</li><br><li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li><br><li>Parameter 4: fonts, separated by commas (,).</li><br><li>Parameter 5: font style. Available options are ("normal", "italic").</li><br><li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: array of five parameters of the string type, separated by semicolons (;).</li> <li>Parameter 1: font color, in #ARGB format.</li> <li>Parameter 2: font size, in fp. The value is a number.</li> <li>Parameter 3: font weight. Available options are ("bold", "normal", "bolder", "lighter", "medium", "regular").</li> <li>Parameter 4: fonts, separated by commas (,).</li> <li>Parameter 5: font style. Available options are ("normal", "italic").</li> <li>Example: "#ff182431;14;normal;Arial,HarmonyOS Sans;normal".</li> </ul>

**Since**: 12

### NODE_TIME_PICKER_START

```c
NODE_TIME_PICKER_START = 14005
```

**Description**

Defines the start time of the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: time. The default value is <b>"00:00:00"</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: time. The default value is <b>"00:00:00"</b>.</li> </ul>

**Since**: 18

### NODE_TIME_PICKER_END

```c
NODE_TIME_PICKER_END = 14006
```

**Description**

Defines the end time of the time picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: time. The default value is <b>"23:59:59"</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: time. The default value is <b>"23:59:59"</b>.</li> </ul>

**Since**: 18

### NODE_TIME_PICKER_ENABLE_CASCADE

```c
NODE_TIME_PICKER_ENABLE_CASCADE = 14007
```

**Description**

Defines whether the AM/PM option is cascaded with the time in 12-hour mode. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable cascade. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable cascade.</li> </ul>

**Since**: 18


