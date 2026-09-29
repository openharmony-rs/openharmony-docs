# CommonOptions

```TypeScript
export declare class CommonOptions
```

Defines the common options of the date and time picker.

> **NOTE:** 
> 
> - The parameter order of the **Date** constructor is: year, month index (0-11), day, hour, minute, second. Note:The year parameter must be greater than 99 or less than 0 to avoid 1900s mapping.
> 
> - For the usage of **Date**, see [TimePickerOptions](../arkts-components/arkts-arkui-timepicker-comp-timepickeroptions-i.md). Note that when you need to set a year between 1 and 99, do not use the **new Date(1, 0, 1)** syntax. The JavaScript **new Date(year, month, day)**constructor has special handling for years 1-99: it automatically adds 1900 to the input year, which results in the year 1901 instead of the intended year 1. In this case, use the **new Date('0001-01-01')** syntax instead.
> 
> - The text font size of **DatePickerComponent** varies with the total number of displayed columns. When the number of columns is 6 or more, the font size is 14 vp; otherwise, it is 16 vp. Text truncation may occur when the component width is too narrow.
> 
> - When a parameter is omitted or set to **undefined**, the default value is used.
> 
> - When **start**, **end**, and **selected** in [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md) are set, only the date part (year,month, day) takes effect. When they are set in [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md), only the time part (hour, minute,second) takes effect. The system automatically filters the corresponding parts of the **Date** object and applies constraints based on the configured **displayMode** and the corresponding **Options** type.

> **NOTE:** 
> 
> - **onChange** is triggered when the user selects a date or time, and is used to respond to the user's selection.
> 
> - **onScrollStop** is triggered after scrolling completely stops, and returns the current selected item regardless of whether the value has changed.
> 
> - Both can be used together or separately as needed: **onChange** is used for immediate response to user selection,and **onScrollStop** is used to obtain the stable result after scrolling stops.
> 
> **NOTE:** 
> 
> Exception handling for the start date, end date, and selected date:
> 
> - If the start date is later than the end date, and the selected date is not set, the start date, end date, and selected date all use the default values.
> 
> - If the start date is later than the end date, and the selected date is earlier than the default start date, the start date and end date use the default values, and the selected date uses the default start date.
> 
> - If the start date is later than the end date, and the selected date is later than the default end date, the start date and end date use the default values, and the selected date uses the default end date.
> 
> - If the start date is later than the end date, and the selected date is within the range of the default start date and default end date, the start date and end date use the default values, and the selected date uses the set value.
> 
> - If the selected date is earlier than the start date, the selected date is set to the start date.
> 
> - If the selected date is later than the end date, the selected date is set to the end date.
> 
> - If the start date is later than the current system date, and the selected date is not set, the selected date is set to the start date.
> 
> - If the end date is earlier than the current system date, and the selected date is not set, the selected date is set to the end date.
> 
> - If the **Date** object constructor parameters are invalid or non-compliant, for example, the year, month, or day parameters are out of the valid range, or an invalid string is passed, resulting in an invalid date, the default value is used.
> 
> - If the start date or end date is earlier than the minimum value of the valid range, the start date or end date uses the default start date.
> 
> - If the start date or end date is later than the maximum value of the valid range, the start date or end date uses the default end date.
> 
> - If both the start date and end date are earlier than the minimum value of the valid range, the start date and end date use the earliest date in the system valid range.
> 
> - If both the start date and end date are later than the maximum value of the valid range, the start date and end date use the latest date in the system valid range.
> 
> **NOTE:** 
> 
> Exception handling for the start time and end time:
> 
> - If the start time is later than the end time, the start time and end time both use the default values.
> 
> - If the selected time is earlier than the start time, the selected time is set to the start time.
> 
> - If the selected time is later than the end time, the selected time is set to the end time.
> 
> - If the start time is later than the current system time, and the selected time is not set, the selected time is set to the start time.
> 
> - If the end time is earlier than the current system time, and the selected time is not set, the selected time is set to the end time.
> 
> - If the **Date** object constructor parameters are invalid or non-compliant, for example, the hour, minute, or second parameters are out of the valid range, or an invalid string is passed, resulting in an invalid date, the default value is used.

**Since:** 26.0.0

<!--Device-unnamed-export declare class CommonOptions--><!--Device-unnamed-export declare class CommonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Whether to enable haptic feedback.

Default value: **true**

- **true**: Haptic feedback is enabled, applicable to scenarios where enhanced user interaction experience is  
needed, such as gaming and musical instrument applications.  
- **false**: Haptic feedback is disabled, applicable to scenarios where haptic feedback is not required or device  
resources need to be conserved.

**NOTE:** 

1. When this parameter is set to **true**, whether it takes effect depends on whether the system hardware
supports it.
2. To enable haptic feedback, configure the **requestPermissions** field in the
[module.json5](../../../quick-start/module-configuration-file.md) file of the project to request the vibration permission. The configuration is as follows:

**"requestPermissions": [{"name": "ohos.permission.VIBRATE"}]**

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-enableHapticFeedback?: boolean--><!--Device-CommonOptions-enableHapticFeedback?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End date or time of the picker.

Default value: **Date('2100-12-31T23:59:59')**

Value range: [Date('0001-01-01T00:00:00'), Date('9999-12-31T23:59:59')]

**NOTE:** 

When **end** is set to a valid value, **loop** does not take effect.

**Type:** Date

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-end?: Date--><!--Device-CommonOptions-end?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: boolean
```

Whether to enable loop mode.

- **true**: Loop mode is enabled, allowing continuous cyclic selection when scrolling to the boundary.  
- **false**: Loop mode is disabled, and scrolling stops at the boundary.

Default value: **true**

**Use scenarios:**

Loop mode is applicable to scenarios requiring continuous scrolling selection, such as quickly browsing years and months. Non-loop mode is applicable to scenarios requiring clear boundary ranges.

**NOTE:** 

When [start](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) or [end](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) is set to a valid value, this parameter does not take effect.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-loop?: boolean--><!--Device-CommonOptions-loop?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<DatePickerComponentResult>
```

Callback triggered when a date or time is selected.

**Type:** Callback&lt;[DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-onChange?: Callback<DatePickerComponentResult>--><!--Device-CommonOptions-onChange?: Callback<DatePickerComponentResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<DatePickerComponentResult>
```

Callback triggered when the picker item is selected and scrolling stops.

**Type:** Callback&lt;[DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-onScrollStop?: Callback<DatePickerComponentResult>--><!--Device-CommonOptions-onScrollStop?: Callback<DatePickerComponentResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Selected date or time, displayed as the initial selected value after being set.

Default value: current system date or time.

**NOTE:** 

In the **DateMode.MONTH_AND_DAY** mode, only the **month** and **day** fields can be selected. The **year** field is specified by **selected**; if no value is specified, the current system year is used and remains unchanged during scrolling.

**Type:** Date

**Default:** current system date or time

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-selected?: Date--><!--Device-CommonOptions-selected?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start date or time of the picker.

Default value: **Date('1970-01-01T00:00:00')**

Value range: [Date('0001-01-01T00:00:00'), Date('9999-12-31T23:59:59')]

**NOTE:** 

When **start** is set to a valid value, **loop** does not take effect.

**Type:** Date

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CommonOptions-start?: Date--><!--Device-CommonOptions-start?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
