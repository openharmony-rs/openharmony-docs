# AlertDialogParamWithButtons

Inherited from [AlertDialogParam](arkts-arkui-alertdialogparam-i.md).

**Inheritance/Implementation:** AlertDialogParamWithButtons extends [AlertDialogParam](arkts-arkui-alertdialogparam-i.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton: AlertDialogButtonBaseOptions
```

Information about the primary button, including the enabling status, default focus, button style, text content, text color, button background color, and click callback. When the dialog box has focus and focus has not been shifted using the **Tab** key, the button responds to the **Enter** key by default, and multiple dialog boxes can gain focus consecutively to respond automatically. The default response to the **Enter** key does not work when **defaultFocus** is set to **true**. For details, see [Example 7](../../../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md#example-7-customizing-the-background-blur-effect).

**Type:** [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton: AlertDialogButtonBaseOptions
```

Information about the secondary button, including the enabling status, default focus, button style, text content, text color, button background color, and click callback.

**Type:** [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
