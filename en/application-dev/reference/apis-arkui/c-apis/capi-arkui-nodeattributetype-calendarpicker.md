# Calendarpicker

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

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

Date of the selected item in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: selected year. Default value: the current system year. The default value is used when an invalid value is passed in.</li> <li>.value[1].u32: selected month. Default value: the current system month. The default value is used when an invalid value is passed in.</li> <li>.value[2].u32: selected day. Default value: the current system date. The default value is used when an invalid value is passed in.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: selected year.</li> <li>.value[1].u32: selected month.</li> <li>.value[2].u32: selected day.</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_EDGE_ALIGNMENT

```c
NODE_CALENDAR_PICKER_EDGE_ALIGNMENT
```

**Description**

How the calendar picker is aligned with the entry component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-picker-h.md#arkui_calendaralignment). It is used to set the alignment position of the calendar picker relative to the entry component.</li> <li>.value[1]?.f32: offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode, in vp. Default value: <b>0</b>.</li> <li>.value[2]?.f32: offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode, in vp. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: alignment mode. The parameter type is [ArkUI_CalendarAlignment](capi-picker-h.md#arkui_calendaralignment).</li> <li>.value[1].f32: offset of the picker relative to the entry component along the x-axis after alignment based on the specified alignment mode, in vp.</li> <li>.value[2].f32: offset of the picker relative to the entry component along the y-axis after alignment based on the specified alignment mode, in vp.</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_TEXT_STYLE

```c
NODE_CALENDAR_PICKER_TEXT_STYLE
```

**Description**

Text color, font size, and font weight in the entry area of the calendar picker.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.u32: text color of the entry area. When not set or after <b>resetAttribute</b> is executed, the value resolved by the system theme <b>calendar_picker_entry_font_color</b> is used (the specific color value varies with the theme and can be obtained through <b>getAttribute</b>).</li> <li>.value[1]?.f32: font size of the entry area, in fp. When not set or after <b>resetAttribute</b> is executed, the value resolved by the system theme <b>calendar_picker_entry_font_size</b> is used (the specific value varies with the theme and can be obtained through <b>getAttribute</b>).</li> <li>.value[2]?.i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). When not set or after <b>resetAttribute</b> is executed, the default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: text color of the entry area.</li> <li>.value[1].f32: font size of the entry area, in fp.</li> <li>.value[2].i32: font weight of the entry area. The parameter type is [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> </ul>

**Since**: 12

### NODE_CALENDAR_PICKER_START

```c
NODE_CALENDAR_PICKER_START = 16004
```

**Description**

Start date of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The value format is "YYYY-MM-DD", where <b>YYYY</b> supports 1 or 4 digits, and <b>MM</b> and <b>DD</b> are 1-2 digit numbers, for example, "1970-1-1" or "2024-05-20". Default value: <b>1970-1-1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: start date of the calendar picker to set, in the format of "YYYY-MM-DD".</li> </ul>

**Since**: 18

### NODE_CALENDAR_PICKER_END

```c
NODE_CALENDAR_PICKER_END = 16005
```

**Description**

End date of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: date. The value format is "YYYY-MM-DD", where <b>YYYY</b> supports 1 or 4 digits, and <b>MM</b> and <b>DD</b> are 1-2 digit numbers, for example, "2100-12-31" or "2025-1-25". Default value: <b>"2100-12-31"</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: end date of the calendar picker to set, in the format of "YYYY-MM-DD".</li> </ul>

**Since**: 18

### NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE

```c
NODE_CALENDAR_PICKER_DISABLED_DATE_RANGE = 16006
```

**Description**

Disabled date ranges of the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: string representing the disabled date ranges. The format is "start_date,end_date" for each range, with multiple ranges separated by commas (,).<br> Format of the disabled date range: "1910-01-01,1910-12-31,2020-01-01,2020-12-31". Default value: empty string, indicating that no disabled date range is set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: string representing the disabled date ranges. The format is "start_date,end_date" for each range, with multiple ranges separated by commas (,), for example, <b>"1910-01-01,1910-12-31"</b>.</li> </ul>

**Since**: 19

### NODE_CALENDAR_PICKER_MARK_TODAY

```c
NODE_CALENDAR_PICKER_MARK_TODAY = 16007
```

**Description**

Whether to highlight the current system date in the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to highlight the current system date in the calendar picker. <b>1</b> to highlight; <b>0</b> otherwise.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the current system date is highlighted in the calendar picker.</li> </ul>

**Since**: 19

### NODE_CALENDAR_PICKER_FIRST_DAY_OF_WEEK

```c
NODE_CALENDAR_PICKER_FIRST_DAY_OF_WEEK = 16008
```

**Description**

Defines the first day of the week for the calendar picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>value[0].i32: first day of the week. The value range is [0, 7]. <b>0</b>: follows the system region. <b>1</b>: Monday. <b>2</b>: Tuesday. <b>3</b>: Wednesday. <b>4</b>: Thursday. <b>5</b>: Friday. <b>6</b>: Saturday. <b>7</b>: Sunday. The default value is <b>0</b> (follows the system region).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>value[0].i32: first day of the week.</li> </ul>

**Since**: 26.2.0


