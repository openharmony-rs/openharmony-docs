# TimePickerDialog

```TypeScript
declare class TimePickerDialog
```

* A time picker dialog box is a dialog box that allows users to select a time from the 24-hour range through scrolling. This component is applicable to scenarios where users need to select a time, such as setting an alarm clock, scheduling, or booking a time. This component provides intuitive time selection interaction, supports switching between the 12-hour format and 24-hour format, and allows you to customize the style and layout, helping your app quickly implement the time selection function and improving user experience.

**Since:** 8

<!--Device-unnamed-declare class TimePickerDialog--><!--Device-unnamed-declare class TimePickerDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TimePickerDialogOptions)
```

Shows a time picker dialog box.

> **NOTE:** 
> 
> Since API version 10, you can use the
> [showTimePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtimepickerdialog) API in
> [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the time picker dialog box is shown in the intended
> UI instance.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [showTimePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtimepickerdialog)

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialog-static show(options?: TimePickerDialogOptions)--><!--Device-TimePickerDialog-static show(options?: TimePickerDialogOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](arkts-arkui-timepicker-comp-timepickerdialogoptions-i.md) | No | Parameters of the time picker dialog box. If the parameter is not specified, the dialog box is not displayed. |
