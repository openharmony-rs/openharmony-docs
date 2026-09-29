# TextPickerDialog

```TypeScript
declare class TextPickerDialog
```

Creates a text picker based on the specified selection range and displays it in a dialog box. This component is applicable to scenarios where users need to select text from preset options, such as setting pages, entering data in AbilityForm, and filtering data.

**Since:** 8

<!--Device-unnamed-declare class TextPickerDialog--><!--Device-unnamed-declare class TextPickerDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TextPickerDialogOptions)
```

Shows a text picker in the given settings.

> **NOTE:** 
> 
> Since API version 10, you can use the
> [showTextPickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtextpickerdialog) API in
> [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the text picker dialog box is shown in the intended
> UI instance.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [showTextPickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtextpickerdialog)

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialog-static show(options?: TextPickerDialogOptions)--><!--Device-TextPickerDialog-static show(options?: TextPickerDialogOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](arkts-arkui-textpicker-comp-textpickerdialogoptions-i.md) | No | Parameters of the text picker dialog box. The dialog can be properly displayed only when the range parameter is provided. Other parameters are optional. |
