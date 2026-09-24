# Calendarpicker

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CALENDAR_PICKER_HINT_RADIUS

```c
NODE_CALENDAR_PICKER_HINT_RADIUS = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER
```

**Description**

Defines the style of the background in the selected state of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: style of the background in the selected state of the calendar picker. The value range is [0, +∞). If the value is <b>0</b>, the background is a rectangle with square corners. If the value is in the 0–16 range, the background is a rectangle with rounded corners. If the value is equal to or greater than 16, the background is a circle.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: style of the background in the selected state of the calendar picker. The value range is [0, +∞). If the value is <b>0</b>, the background is a rectangle with square corners. If the value is in the 0–16 range, the background is a rectangle with rounded corners. If the value is equal to or greater than 16, the background is a circle.</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_SELECTED_DATE

```c
NODE_CALENDAR_PICKER_SELECTED_DATE
```

**Description**

Defines the date of the selected item in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: year of the selected date.</li> <li>.value[1].u32: month of the selected date.</li> <li>.value[2].u32: day of the selected date.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: year of the selected date.</li> <li>.value[1].u32: month of the selected date.</li> <li>.value[2].u32: day of the selected date.</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_EDGE_ALIGNMENT

```c
NODE_CALENDAR_PICKER_EDGE_ALIGNMENT
```

**Description**

Defines how the calendar picker is aligned with the entry component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-picker-h.md#arkui_calendaralignment).</li> <li>.value[1]?.f32: offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode.</li> <li>.value[2]?.f32: offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-picker-h.md#arkui_calendaralignment).</li> <li>.value[1]?.f32: offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode.</li> <li>.value[2]?.f32: offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode.</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_TEXT_STYLE

```c
NODE_CALENDAR_PICKER_TEXT_STYLE
```

**Description**

Defines the font color, font size, and font weight in the entry area of the calendar picker.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.u32: font color of the entry area.</li> <li>.value[1]?.f32: font size of the entry area, in fp.</li> <li>.value[2]?.i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: font color of the entry area.</li> <li>.value[1].f32: font size of the entry area, in fp.</li> <li>.value[2].i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_START

```c
NODE_CALENDAR_PICKER_START = 16004
```

**Description**

Defines the start date of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The value like <b>"1970-1-1"</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: date.</li> </ul>

**Since**: 18

### NODE_CALENDAR_PICKER_END

```c
NODE_CALENDAR_PICKER_END = 16005
```

**Description**

Defines the end date of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The value like <b>"2100-12-31"</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: date.</li> </ul>

**Since**: 18

### NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE

```c
NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006
```

**Description**

Defines the disabled date range of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: A string of dates. The `1st start date`,`1st end date`,`2nd start date`,`2nd end date`, ...,`nth start date`,`nth end date` of the disabled date range.</li> <li> Example: 1910-01-01,1910-12-31,2020-01-01,2020-12-31</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: A string of dates.</li> </ul>

**Since**: 19

### NODE_CALENDAR_PICKER_MARK_TODAY

```c
NODE_CALENDAR_PICKER_MARK_TODAY = 16007
```

**Description**

Defines whether the calendar picker marks today. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>value[0].i32: whether the calendar picker marks today. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>value[0].i32: whether the calendar picker marks today.</li> </ul>

**Since**: 19


