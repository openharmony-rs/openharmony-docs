# DatePickerOptions

```TypeScript
declare interface DatePickerOptions
```

Describes the parameters of the date picker.

> **NOTE:** 
> 
> - For details about how to use **Date**, see [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md).
> 
> - Property modifications made to **DatePickerOptions** during the **DatePicker** scrolling process may not take effect.

> **NOTE:** 
> 
> Handle exceptions for the start and end dates first, followed by exceptions for the selected date.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End date of the picker.

Default value: **Date('2100-12-31')**

Value range: [Date('1900-01-31'), Date('2100-12-31')].

**Type:** Date

**Default:** 
- API version 11+: Date('2100-12-31')

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DatePickerMode
```

Date display mode.

Default value: **DatePickerMode.DATE**, which means to display three columns: year, month, and day.

In [DatePickerDialog](arkts-arkui-datepicker-comp.md#date_picker), when **showTime** in [DatePickerDialogOptions](arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) is **true**, this parameter is ignored and the year, month, day columns are always shown.

**Type:** [DatePickerMode](arkts-arkui-datepicker-comp-datepickermode-e.md)

**Default:** DatePickerMode.DATE - which means to display three columns: year, month, and day. <br>Decimal values are rounded off.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Date of the selected item.

Default value: current system date.

Value range: [Date('1900-01-31'), Date('2100-12-31')].

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** Date

**Default:** 
- API version 11+: current system date

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start date of the picker.

Default value: **Date('1970-1-1')**

Value range: [Date('1900-01-31'), Date('2100-12-31')].

**Type:** Date

**Default:** 
- API version 11+: Date('1970-1-1')

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
