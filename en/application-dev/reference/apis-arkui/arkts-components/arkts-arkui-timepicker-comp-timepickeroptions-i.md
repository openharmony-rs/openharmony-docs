# TimePickerOptions

```TypeScript
declare interface TimePickerOptions
```

Describes the parameters of the time picker.

Property modifications made to **TimePickerOptions** during the **TimePicker** scrolling process may not take effect.

The **Date** object is used to handle dates and time. It can be used in the following ways:

**Method 1**: new Date()

Obtains the current system date and time.

**Method 2**: new Date(value: number | string)

- **value** (mandatory): number&nbsp;\|&nbsp;string. Sets the date format.

number: milliseconds, the number of milliseconds elapsed since 00:00:00 on January 1, 1970. Value range: [0, +∞).

string: a string in time format, for example, '2025-02-20 08:00:00' or '2025-02-20T08:00:00'.

**Method 3**: new Date(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number)

- **year** (mandatory): number. Year, for example, **2025**.  
- **monthIndex** (mandatory): number. Month index (value range: 0 to 11), where 0 indicates January and 11 indicates  
December. For example, 0 indicates January and 2 indicates March. A value out of range causes a date calculation error.  
- **date** (optional): number. Date, for example, **10** (if **hours** is set, **date** cannot be omitted).  
- **hours** (optional): number. Hour (value range: [0, 23]). A value out of range causes a date calculation error.  
For example, 15 (if minutes is set, hours cannot be omitted). Unit: hour.  
- **minutes** (optional): number. Minute (value range: [0, 59]). A value out of range causes a date calculation  
error. For example, 20 (if seconds is set, minutes cannot be omitted). Unit: minute.  
- **seconds** (optional): number. Second (value range: [0, 59]). A value out of range causes a date calculation  
error. For example, 20 (if ms is set, seconds cannot be omitted). Unit: second.  
- **ms** (optional): number. Millisecond (value range: [0, 999]). A value out of range causes a date calculation  
error. For example, 10. Unit: ms (millisecond).

> **NOTE:** 
> 
> Handling in the case of date configuration exceptions:
> 
> - If the start time is later than the end time, both start time and end time are set to their default values.
> 
> - If the selected time is earlier than the start time, the selected time is set to the start time.
> 
> - If the selected time is later than the end time, the selected time is set to the end time.
> 
> - If the start time is later than the current system time and the selected time is not set, the selected time is set to the start time.
> 
> - If the end time is earlier than the current system time and the selected time is not set, the selected time is set to the end time.
> 
> - If the time format is invalid, such as **'01:61:61'**, the default value is used.

**Since:** 8

<!--Device-unnamed-declare interface TimePickerOptions--><!--Device-unnamed-declare interface TimePickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

Specifies the end time of the TimePicker component.

Default value: the end time is 23:59:59 (hour = 23, minute = 59)

**Note:** 

1. Only the set hour and minute take effect.
2. When start or end is set to a non-default value, loop does not take effect.

**Atomic service API:** Since API version 18, this API is supported in atomic services.

**Type:** Date

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerOptions-end?: Date--><!--Device-TimePickerOptions-end?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## format

```TypeScript
format?: TimePickerFormat
```

Specifies the format of the TimePicker to be displayed.

Default value: TimePickerFormat.HOUR_MINUTE

**Atomic service API:** Since API version 12, this API is supported in atomic services.

**Type:** [TimePickerFormat](arkts-arkui-timepicker-comp-timepickerformat-e.md)

**Default:** HOUR_MINUTE

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerOptions-format?: TimePickerFormat--><!--Device-TimePickerOptions-format?: TimePickerFormat-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Sets the time of the selected item.

Default value: current system time

Since API version 10, this parameter supports [$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding variables.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Date

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerOptions-selected?: Date--><!--Device-TimePickerOptions-selected?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Specifies the start time of the TimePicker component.

Default value: the start time is 00:00:00 (hour = 0, minute = 0)

**Note:** 

1. Only the set hour and minute take effect.
2. When start or end is set to a non-default value, loop does not take effect.

**Atomic service API:** Since API version 18, this API is supported in atomic services.

**Type:** Date

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerOptions-start?: Date--><!--Device-TimePickerOptions-start?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
