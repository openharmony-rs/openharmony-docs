# AlertDialogButtonOptions

```TypeScript
declare interface AlertDialogButtonOptions extends AlertDialogButtonBaseOptions
```

Inherits from [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md).

**Inheritance/Implementation:** AlertDialogButtonOptions extends [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary?: boolean
```

Whether the button responds to the **Enter** key by default when the dialog box has focus and the **Tab** key is not pressed for sequential focus navigation. If there are multiple buttons, set this parameter to **true** for only one button. Otherwise, no button will respond. Multiple dialog boxes can automatically gain focus and respond to user interactions in a sequential manner. This parameter does not take effect when **defaultFocus** is set to **true**. **true**: The button responds to the **Enter** key by default. **false**: The button does not respond to the **Enter** key by default.

Default value: **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
