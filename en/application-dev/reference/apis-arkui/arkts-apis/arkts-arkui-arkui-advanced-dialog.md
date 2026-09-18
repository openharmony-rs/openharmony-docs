# @ohos.arkui.advanced.Dialog

## Modules to Import

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md) | Declare ButtonOptions |

### Structs

| Name | Description |
| --- | --- |
| [AlertDialog](arkts-arkui-arkui-advanced-dialog-alertdialog-s.md) | Declare CustomDialog AlertDialog |
| [ConfirmDialog](arkts-arkui-arkui-advanced-dialog-confirmdialog-s.md) | Declare CustomDialog ConfirmDialog |
| [CustomContentDialog](arkts-arkui-arkui-advanced-dialog-customcontentdialog-s.md) | Declare custom content dialog |
| [LoadingDialog](arkts-arkui-arkui-advanced-dialog-loadingdialog-s.md) | Declare CustomDialog LoadingDialog |
| [PopoverDialog](arkts-arkui-arkui-advanced-dialog-popoverdialog-s.md) | Declare struct PopoverDialog |
| [SelectDialog](arkts-arkui-arkui-advanced-dialog-selectdialog-s.md) | Declare CustomDialog SelectDialog |
| [TipsDialog](arkts-arkui-arkui-advanced-dialog-tipsdialog-s.md) | Declare CustomDialog TipsDialog |

### Interfaces

| Name | Description |
| --- | --- |
| [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md) | Defines PopoverDialog Options |

## Examples

```TypeScript
### Example 1: Dialog Box with an Image Above Text

This example implements a dialog box with an image above the text content, through the use of imageRes, content, and other properties.


```

```TypeScript
### Example 2: List-only Dialog Box

This example presents a dialog box consisting solely of a list defined with selectedIndex and radioContent.


```

```TypeScript
### Example 3: Dialog Box with Text and Check Boxes

This example illustrates a dialog box that combines text content with check boxes defined with content and checkTips.


```

```TypeScript
### Example 4: Text-only Dialog Box

This example demonstrates a simple text-only dialog box defined with primaryTitle, secondaryTitle, and content.


```

```TypeScript
### Example 5: Loading Dialog Box

This example implements a loading dialog box that contains a progress indicator.


```

```TypeScript
### Example 6: Dialog Box with a Custom Theme

This example presents a dialog box with a custom theme, through the use of content, theme, and other properties.


```

```TypeScript
### Example 7: Dialog Box in Custom Color Mode

This example presents a dialog box in the specified light or dark mode, through the use of content, themeColorMode, and other properties.


```

```TypeScript
### Example 8: Dialog Box with Custom Content

This example implements a dialog box with custom content defined with contentBuilder and buttons.


```

```TypeScript
### Example 9: Popover Dialog Box

This example demonstrates a popover dialog box for alert purposes, through the use of visible, popover, targetBuilder, and other properties. This functionality is supported since API version 14.


```

```TypeScript
### Example 10: Setting the Default Focus Button for a Dialog Box

This example demonstrates how to set the button that receives focus by default in a dialog box using AlertDialog, including the defaultFocus property. This functionality is supported since API version 18.
```
