# TimePickerDialog

A time picker dialog box is a dialog box that allows users to select a time from the 24-hour range through scrolling.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TimePickerDialogOptions)
```

Shows a time picker dialog box.

**NOTE:** 

- Since API version 10, you can use the [showTimePickerDialog](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showtimepickerdialog) API in [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the time picker dialog box is shown in the intended UI instance.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [showTimePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtimepickerdialog)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](arkts-arkui-timepickerdialogoptions-i.md) | No | Parameters of the time picker dialog box. |
