# AlertDialog

**Since:** 7

**Deprecated since:** 26.0.0

**Substitutes:** [showAlertDialog](arkts-arkui-arkui-uicontext-uicontext-c.md#showalertdialog)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(value: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions)
```

Shows an alert dialog box.

> **NOTE:** 
> 
> Since API version 10, you can use the
> [showAlertDialog](arkts-arkui-arkui-uicontext-uicontext-c.md#showalertdialog) API in
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the alert dialog box is shown in the intended UI
> instance.

**Since:** 7

**Deprecated since:** 18

**Substitutes:** [showAlertDialog](arkts-arkui-arkui-uicontext-uicontext-c.md#showalertdialog)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) &#124; [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) &#124; [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | Yes | Defines and displays the **AlertDialog** component.<br>**Since:** 10 |
