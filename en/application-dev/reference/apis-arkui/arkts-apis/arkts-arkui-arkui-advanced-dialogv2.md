# @ohos.arkui.advanced.DialogV2

## Modules to Import

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md) | Declare AdvancedDialogV2Button. |

### Structs

| Name | Description |
| --- | --- |
| [AlertDialogV2](arkts-arkui-arkui-advanced-dialogv2-alertdialogv2-s.md) | Declare CustomDialog AlertDialogV2. |
| [ConfirmDialogV2](arkts-arkui-arkui-advanced-dialogv2-confirmdialogv2-s.md) | Declare CustomDialog ConfirmDialogV2 |
| [CustomContentDialogV2](arkts-arkui-arkui-advanced-dialogv2-customcontentdialogv2-s.md) | Declare custom content dialog |
| [LoadingDialogV2](arkts-arkui-arkui-advanced-dialogv2-loadingdialogv2-s.md) | Declare CustomDialog LoadingDialogV2 |
| [PopoverDialogV2](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2-s.md) | Declare struct PopoverDialogV2 |
| [SelectDialogV2](arkts-arkui-arkui-advanced-dialogv2-selectdialogv2-s.md) | Declare CustomDialog SelectDialogV2 |
| [TipsDialogV2](arkts-arkui-arkui-advanced-dialogv2-tipsdialogv2-s.md) | Declare CustomDialog TipsDialogV2 |

### Interfaces

| Name | Description |
| --- | --- |
| [AdvancedDialogV2ButtonOptions](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2buttonoptions-i.md) | Declare the options of AdvancedDialogV2Button |
| [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md) | Defines PopoverDialogV2 Options |

### Types

| Name | Description |
| --- | --- |
| [AdvancedDialogV2ButtonAction](arkts-arkui-advanceddialogv2buttonaction-t.md) | Declare the action when the button of dialog is clicked. |
| [AdvancedDialogV2OnCheckedChange](arkts-arkui-advanceddialogv2oncheckedchange-t.md) | Declare the callback when the checkbox of dialog is changed. |
| [PopoverDialogV2OnVisibleChange](arkts-arkui-popoverdialogv2onvisiblechange-t.md) | Declare the callback when the visibility of PopoverDialogV2 is changed. |

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
### Example 7: Dialog Box with Custom Content

This example implements a dialog box with custom content defined with contentBuilder and buttons.


```

```TypeScript
### Example 8: Popover Dialog Box

This example demonstrates a popover dialog box for alert purposes, through the use of visible, popover, targetBuilder, and other properties.
```
