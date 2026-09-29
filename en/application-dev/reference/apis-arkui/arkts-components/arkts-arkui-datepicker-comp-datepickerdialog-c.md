# DatePickerDialog

```TypeScript
declare class DatePickerDialog
```

Creates a date picker based on the specified date range and displays it in a dialog box. This component is suitable for scenarios where users need to quickly select a date, such as schedule arrangement, activity arrangement, and birthday setting. Using this component simplifies the development process, provides a unified date selection user experience, and supports multiple customization options to meet different requirements.

**Since:** 8

<!--Device-unnamed-declare class DatePickerDialog--><!--Device-unnamed-declare class DatePickerDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: DatePickerDialogOptions)
```

Shows a date picker dialog box.

> **NOTE:** 
> 
> Since API version 10, you can use the
> [showDatePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showdatepickerdialog) API in
> [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the date picker dialog box is shown in the intended
> UI instance.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [showDatePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showdatepickerdialog)

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialog-static show(options?: DatePickerDialogOptions)--><!--Device-DatePickerDialog-static show(options?: DatePickerDialogOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) | No | Parameters for configuring the date picker dialog box. If this parameter is not set, the dialog box is not displayed. |
