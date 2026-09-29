# DatePickerOptions

```TypeScript
declare interface DatePickerOptions
```

Describes the parameters of the date picker.

> **NOTE:** 
> 
> - For details about how to use **Date**, see [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md).
> 
> - Modifying the attributes in **DatePickerOptions** while the **DatePicker** component is scrolling will cause these attributes to fail to take effect.
> 
> - If the start and end dates to be set are outside the range of \[Date('1900-01-31'), Date('2100-12-31')], it is recommended to use [DatePickerComponent](../arkts-apis/arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponent-s.md).
> 
> **NOTE:** 
> 
> Handling in the case of date configuration exceptions:
> 
> - If the start date is later than the end date, and the selected date is not set, the start date, end date, and selected date are set to the default values.
> 
> - If the start date is later than the end date, and the selected date is earlier than the default start date, the start date and end date are set to the default values, and the selected date is set to the default start date.
> 
> - If the start date is later than the end date, and the selected date is later than the default end date, the start date and end date are set to the default values, and the selected date is set to the default end date.
> 
> - If the start date is later than the end date, and the selected date is within the range of the default start date and end date, the start date and end date are set to the default values, and the selected date is set to the specified value.
> 
> - If the selected date is earlier than the start date, the start date is set to the selected date.
> 
> - If the selected date is later than the end date, the end date is set to the selected date.
> 
> - If the start date is later than the current system date, and the selected date is not set, the start date is set to the selected date.
> 
> - If the end date is earlier than the current system date, and the selected date is not set, the end date is set to the selected date.
> 
> - If the set date is in invalid format, for example, **'1999-13-32'**, the default value is used.
> 
> - If the start date or end date is earlier than the earliest date in the valid date range, the start date or end date is set to the default state date.
> 
> - If the start date or end date is later than the latest date in the valid date range, the start date or end date is set to the default end date.
> 
> - If both the start date and end date are earlier than the earliest date in the valid date range, the start date and end date are set to the earliest date in the valid date range.
> 
> - If both the start date and end date are later than the latest date in the valid date range, the start date and end date are set to the latest date in the valid date range.
> 
> **NOTE:** 
> 
> Handle exceptions for the start and end dates first, followed by exceptions for the selected date.

**Since:** 8

<!--Device-unnamed-declare interface DatePickerOptions--><!--Device-unnamed-declare interface DatePickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End date of the picker. It applies to scenarios where the upper limit of selectable dates needs to be restricted, for example, setting the expiration date of a validity period. <!--RP2--><!--RP2End-->

Default value: **Date('2100-12-31')**

Value range: [Date('1900-01-31'), Date('2100-12-31')]

**Note:** 

When **start** or **end** is set to a non-default value, **canLoop** does not take effect.

**Type:** Date

**Default:** 
- API version 11+: Date('2100-12-31')

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerOptions-end?: Date--><!--Device-DatePickerOptions-end?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DatePickerMode
```

Date display mode. It applies to scenarios where the date display columns need to be customized, for example, only the year and month or the month and day need to be selected. If this parameter is not passed, **DatePickerMode.DATE** is used by default, and the year, month, and day columns are displayed.

In [DatePickerDialog](arkts-arkui-datepicker-comp.md), when **showTime** of [DatePickerDialogOptions](arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) is set to **true**, this parameter does not take effect, and the year, month, and day columns are displayed by default. This is to ensure layout rationality, because an additional time column is displayed when **showTime** is set to **true**.

**Note:** 

The preceding **DatePickerDialog**-related restriction applies only to the **DatePickerDialog** component.

**Type:** [DatePickerMode](arkts-arkui-datepicker-comp-datepickermode-e.md)

**Default:** DatePickerMode.DATE - which means to display three columns: year, month, and day. <br>Decimal values are rounded off.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerOptions-mode?: DatePickerMode--><!--Device-DatePickerOptions-mode?: DatePickerMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Date of the selected item. It applies to scenarios where an initial selected date needs to be preset, for example, editing an existing record or displaying a specified date by default.

Default value: current system date (affected by the **start** and **end** parameters; see the abnormal situation description below for details).

Configurable date range of the **Date** object: [Date('1900-01-31'), Date('2100-12-31')]. The valid range of the **selected** parameter: it must be within the date range set by the **start** and **end** parameters.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** Date

**Default:** 
- API version 11+: current system date

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerOptions-selected?: Date--><!--Device-DatePickerOptions-selected?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start date of the picker. It applies to scenarios where the lower limit of selectable dates needs to be restricted, for example, only dates after a certain date are allowed to be selected. <!--RP1--><!--RP1End-->

Default value: **Date('1970-01-01')**

Value range: [Date('1900-01-31'), Date('2100-12-31')]

**Note:** 

When **start** or **end** is set to a non-default value, **canLoop** does not take effect.

**Type:** Date

**Default:** 
- API version 11+: Date('1970-1-1')

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerOptions-start?: Date--><!--Device-DatePickerOptions-start?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
