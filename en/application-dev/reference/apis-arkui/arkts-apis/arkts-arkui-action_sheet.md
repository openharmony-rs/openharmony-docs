# action_sheet(ActionSheet)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ActionSheet](arkts-arkui-actionsheet-c.md) |  |

### Interfaces

| Name | Description |
| --- | --- |
| [ActionSheetButtonOptions](arkts-arkui-actionsheetbuttonoptions-i.md) | Provides button style configuration for the dialog box. |
| [ActionSheetOffset](arkts-arkui-actionsheetoffset-i.md) | Alignment mode of the dialog box. |
| [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | Provides **ActionSheet** configuration options. |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | Provides information about the action to dismiss the dialog box. |
| [SheetInfo](arkts-arkui-sheetinfo-i.md) | Defines the option content in the dialog box. You can configure the text, icon, and callback for each option. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ActionSheetOptions](arkts-arkui-actionsheetoptions-i-sys.md) | Provides **ActionSheet** configuration options. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [ImmersiveMode](arkts-arkui-immersivemode-t.md) | Defines the overlay effect for the dialog box. |
| [LevelMode](arkts-arkui-levelmode-t.md) | Defines the display level mode for the dialog box. |

## Examples

```TypeScript
### Example 1: Displaying an Action Sheet

This example demonstrates how to display an action sheet when a button is touched.


```

```TypeScript
### Example 2: Opening a Dialog Box Outside the Main Window

This example demonstrates how to configure a dialog box to display outside the main window on a 2-in-1 device by setting [showInSubWindow](arkts-arkui-actionsheetoptions-i.md) to true.


```

```TypeScript
### Example 3: Setting the Dialog Box Animation

This example illustrates how to use the [transition](arkts-arkui-actionsheetoptions-i.md) API to create custom animation effects for the dialog box's appearance and disappearance.


```

```TypeScript
### Example 4: Setting the Dialog Box Style

This example demonstrates how to set styles of a dialog box, including the width, height, background color, and shadow.


```

```TypeScript
### Example 5: Configuring a Dialog Box in the Hover State
```

```TypeScript
### Example 6: Using Dialog Box Lifecycle Callbacks

This example demonstrates how to configure the lifecycle callbacks for the dialog box.

The onDidAppear, onDidDisappear, onWillAppear, and onWillDisappear properties are supported in [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) since API version 19.


```

```TypeScript
### Example 7: Customizing the Background Blur Effect

This example demonstrates how to customize the background blur effect by configuring [backgroundBlurStyleOptions](arkts-arkui-actionsheetoptions-i.md).

The backgroundBlurStyleOptions property is supported in [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) since API version 19.


```

```TypeScript
### Example 8: Customizing the Background Effect

This example demonstrates how to customize the background effect by configuring [backgroundEffect](arkts-arkui-actionsheetoptions-i.md).

The backgroundEffect property is supported in [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) since API version 19.


```

```TypeScript
### Example 9: Setting the System Material of the Dialog Box

This example implements the system material effect by configuring the systemMaterial attribute in [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md).

Since API version 26.0.0, the systemMaterial attribute has been added to [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md).
```
