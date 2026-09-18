# custom_dialog_controller(CustomDialog)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CustomDialogController](arkts-arkui-customdialogcontroller-c.md) | Defines the controller of the custom dialog box. |

### Interfaces

| Name | Description |
| --- | --- |
| [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md) | Defines the style of the custom dialog box. |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | Provides information about the action to dismiss the dialog box. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i-sys.md) | Defines the style of the custom dialog box. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [PromptActionCommonState](arkts-arkui-promptactioncommonstate-t.md) | Defines the state of the custom dialog box. |

## Examples

```TypeScript
### Example 1: Opening Nested Dialog Boxes

This example demonstrates how to open one or more custom dialog boxes within another custom dialog box.
```

```TypeScript
### Example 2: Opening a Dialog Box Outside the Main Window

This example demonstrates how to configure a dialog box to display outside the main window on a 2-in-1 device by setting [showInSubWindow](arkts-arkui-customdialogcontrolleroptions-i.md) to true.

Since API version 26.0.0, the displayModeInSubWindow attribute is added to [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md).


```

```TypeScript
### Example 3: Setting the Dialog Box Style

This example demonstrates how to set styles of a custom dialog box, including the width, height, background color, and shadow.


```

```TypeScript
### Example 4: Configuring a Dialog Box in the Hover State
```

```TypeScript
### Example 5: Obtaining the Dialog Box State

This example demonstrates how to call getState in [CustomDialogController](arkts-arkui-customdialogcontroller-c.md) to obtain the current status of the dialog box.

The getState API is added to CustomDialogController since API version 20.
```

```TypeScript
### Example 6: Using @Link and @Consume to Listen for Data Changes

This example uses @[Link](../../../ui/state-management/arkts-link.md) and @[Consume](../../../ui/state-management/arkts-provide-and-consume.md) to implement two-way data binding between the page and the dialog box.


```

```TypeScript
### Example 7: Customizing a Loading Dialog Box

This example uses [maskColor](arkts-arkui-customdialogcontrolleroptions-i.md), [maskRect](arkts-arkui-customdialogcontrolleroptions-i.md), and [LoadingProgress](ts-basic-components-loadingprogress.md) to implement a loading dialog box and display the transparent transmission effect of events that are not in the maskRect area.


```

```TypeScript
### Example 8: Adjusting Spacing Between the Dialog Box and the Soft Keyboard Without keyboardAvoidDistance

This example demonstrates how to listen for keyboard changes and adjust the [bottom](ts-types.md#margin) of [margin](ts-universal-attributes-size.md#margin) to achieve the same effect as using [keyboardAvoidDistance](arkts-arkui-customdialogcontrolleroptions-i.md) to adjust the spacing between the dialog box and the soft keyboard.

Since API version 15, the keyboardAvoidDistance attribute is added to CustomDialogControllerOptions.
```

```TypeScript
### Example 9: Configuring the Lifecycle Callback for the Dialog Box

This example demonstrates how to configure the lifecycle callbacks for the dialog box.

Since API version 19, the onDidAppear, onDidDisappear, onWillAppear, and onWillDisappear attributes are added to [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md).


```

```TypeScript
### Example 10: Implementing Dialog Boxes with Different customStyle Values

This example demonstrates the display effects of dialog content and safe areas under different [customStyle](arkts-arkui-customdialogcontrolleroptions-i.md) values when the alignment mode is [DialogAlignment.Bottom](ts-methods-alert-dialog-box.md#dialogalignment).


```

```TypeScript
### Example 11: Customizing the Background Blur Effect

This example demonstrates how to customize the background blur effect by configuring [backgroundBlurStyleOptions](arkts-arkui-customdialogcontrolleroptions-i.md).

Since API version 19, the backgroundBlurStyleOptions attribute is added to [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md).


```

```TypeScript
### Example 12: Customizing the Background Effect

This example demonstrates how to customize the background effect by configuring [backgroundEffect](arkts-arkui-customdialogcontrolleroptions-i.md).

Since API version 19, the backgroundEffect attribute is added to [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md).


```

```TypeScript
### Example 13: Dynamically Updating the Custom Dialog Box Width

This example demonstrates how to dynamically update the custom dialog box width by synchronizing the custom component's width with a state variable.


```

```TypeScript
### Example 14: Setting the System Material of a Dialog box

This example demonstrates how to implement the system material effect by setting [systemMaterial](arkts-arkui-customdialogcontrolleroptions-i.md).

Since API version 26.0.0, the systemMaterial attribute is added to [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md).
```
