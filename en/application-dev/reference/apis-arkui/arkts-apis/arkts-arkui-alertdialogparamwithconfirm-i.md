# AlertDialogParamWithConfirm

```TypeScript
declare interface AlertDialogParamWithConfirm extends AlertDialogParam
```

Inherited from [AlertDialogParam](arkts-arkui-alertdialogparam-i.md).

Priorities of the **confirm** parameters: **fontColor** and **backgroundColor**  
> **style**
> **defaultFocus**

**Inheritance/Implementation:** AlertDialogParamWithConfirm extends [AlertDialogParam](arkts-arkui-alertdialogparam-i.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
confirm?: AlertDialogButtonBaseOptions
```

Information about the confirm button. When the dialog box has focus and the **Tab** key is not pressed for sequential focus navigation, the button responds to the **Enter** key by default. Multiple dialog boxes can automatically gain focus and respond to user interactions in a sequential manner. The default response to the **Enter** key does not work when **defaultFocus** is set to **true**.

**Type:** [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
