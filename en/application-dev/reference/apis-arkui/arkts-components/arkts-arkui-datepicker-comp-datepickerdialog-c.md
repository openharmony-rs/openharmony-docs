# DatePickerDialog

```TypeScript
declare class DatePickerDialog
```

Defines DatePickerDialog which uses show method to show DatePicker dialog.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: DatePickerDialogOptions)
```

Shows a date picker dialog box.

> **NOTE:** 
> 
> Since API version 10, you can use the
> [showDatePickerDialog](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showdatepickerdialog) API
> in [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the date picker dialog box is shown in the
> intended UI instance.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [showDatePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showdatepickerdialog)

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) | No | Parameters of the date picker dialog box. |
