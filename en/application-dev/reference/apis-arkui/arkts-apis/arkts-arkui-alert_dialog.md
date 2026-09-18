# alert_dialog(AlertDialog)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AlertDialog](arkts-arkui-alertdialog-c.md) |  |

### Interfaces

| Name | Description |
| --- | --- |
| [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md) | Defines the button style of the alert dialog box. |
| [AlertDialogButtonOptions](arkts-arkui-alertdialogbuttonoptions-i.md) | Inherits from [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md). |
| [AlertDialogParam](arkts-arkui-alertdialogparam-i.md) | Enumerates the alert dialog box styles. |
| [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) | Inherited from [AlertDialogParam](arkts-arkui-alertdialogparam-i.md). |
| [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) | Inherited from [AlertDialogParam](arkts-arkui-alertdialogparam-i.md). |
| [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | Inherited from [AlertDialogParam](arkts-arkui-alertdialogparam-i.md). |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | Provides information about the action to dismiss the dialog box. |
| [TextStyle](arkts-arkui-textstyle-i.md) | Describes the word break rule of the message in the dialog box. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AlertDialogParam](arkts-arkui-alertdialogparam-i-sys.md) | Enumerates the alert dialog box styles. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DialogAlignment](arkts-arkui-dialogalignment-e.md) | Enumerates the alignment modes of the alert dialog boxes. |
| [DialogButtonDirection](arkts-arkui-dialogbuttondirection-e.md) | Enumerates the alignment modes of the buttons in the alert dialog box. |

### Types

| Name | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-levelorder-t.md) | Defines the display order of the dialog box. |

## Examples

```TypeScript
### Example 1: Displaying Dialog Boxes with Different Numbers of Buttons

This example uses [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md), [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md), and [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) to display dialog boxes with one, two, and three buttons, respectively.


```

```TypeScript
### Example 2: Opening a Dialog Box Outside the Main Window

This example demonstrates how to configure a dialog box to display outside the main window on a 2-in-1 device by setting showInSubWindow in [AlertDialogParam](arkts-arkui-alertdialogparam-i.md) to true.


```

```TypeScript
### Example 3: Setting the Dialog Box Animation

This example demonstrates how to use the transition attribute in [AlertDialogParam](arkts-arkui-alertdialogparam-i.md) to create animation effects for the dialog box's appearance and disappearance.


```

```TypeScript
### Example 4: Setting the Dialog Box Style

This example demonstrates how to set styles of an alert dialog box, including the width, height, background color, and shadow.


```

```TypeScript
### Example 5: Configuring a Dialog Box in the Hover State
```

```TypeScript
### Example 6: Using Dialog Box Lifecycle Callbacks

This example demonstrates the usage of dialog box lifecycle callbacks.


```

```TypeScript
### Example 7: Customizing the Background Blur Effect

This example demonstrates how to customize the background blur effect by setting backgroundBlurStyleOptions in [AlertDialogParam](arkts-arkui-alertdialogparam-i.md).

The backgroundBlurStyleOptions attribute is added to AlertDialogParam since API version 19.


```

```TypeScript
### Example 8: Customizing the Background Effect

This example demonstrates how to customize the background effect by setting backgroundEffect in [AlertDialogParam](arkts-arkui-alertdialogparam-i.md).

The backgroundEffect attribute is added to AlertDialogParam since API version 19.


```

```TypeScript
### Example 9: Setting the System Material of the Dialog Box

This example implements the system material effect by configuring the systemMaterial attribute in [AlertDialogParam](arkts-arkui-alertdialogparam-i.md).

Since API version 26.0.0, the systemMaterial attribute is added to AlertDialogParam.
```
