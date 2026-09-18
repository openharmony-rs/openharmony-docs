# AlertDialogParamWithOptions

Inherited from [AlertDialogParam](arkts-arkui-alertdialogparam-i.md).

**Inheritance/Implementation:** AlertDialogParamWithOptions extends [AlertDialogParam](arkts-arkui-alertdialogparam-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonDirection

```TypeScript
buttonDirection?: DialogButtonDirection
```

Button layout direction. The default value is **DialogButtonDirection.AUTO**. You are advised to use the auto mode for more than three buttons. (Vertical layout is used for more than two buttons, typically accommodating more buttons.) In non-auto mode, more than three buttons may not be completely displayed, and the buttons that exceed the display range will be truncated.

**Type:** [DialogButtonDirection](arkts-arkui-dialogbuttondirection-e.md)

**Default:** DialogButtonDirection.AUTO

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: Array<AlertDialogButtonOptions>
```

Buttons in the dialog box.

**Type:** Array&lt;[AlertDialogButtonOptions](arkts-arkui-alertdialogbuttonoptions-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
