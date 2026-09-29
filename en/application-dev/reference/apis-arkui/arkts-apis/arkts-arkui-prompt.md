# @ohos.prompt(Prompt)

The **Prompt** module provides APIs for creating and showing toasts, dialog boxes, and action menus.

> **NOTE:** 
> 
> The APIs of this module are deprecated since API Version 9. You are advised to use
> [@ohos.promptAction](arkts-arkui-promptaction-n.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [promptAction](arkts-arkui-promptaction-n.md)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-unnamed-declare namespace prompt--><!--Device-unnamed-declare namespace prompt-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [showActionMenu](arkts-arkui-prompt-showactionmenu-f.md#showactionmenu) | Shows an action menu. This API uses a callback to return the result asynchronously. |
| [showActionMenu](arkts-arkui-prompt-showactionmenu-f.md#showactionmenu-1) | Shows an action menu. This API uses a promise to return the result. |
| [showDialog](arkts-arkui-prompt-showdialog-f.md#showdialog) | Shows a dialog box. This API uses an asynchronous callback to return the result. |
| [showDialog](arkts-arkui-prompt-showdialog-f.md#showdialog-1) | Shows a dialog box. This API uses a promise to return the result. |
| [showToast](arkts-arkui-prompt-showtoast-f.md) | Shows a toast. |

### Interfaces

| Name | Description |
| --- | --- |
| [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | Describes the options for showing the action menu. |
| [ActionMenuSuccessResponse](arkts-arkui-prompt-actionmenusuccessresponse-i.md) | Describes the action menu response result. |
| [Button](arkts-arkui-prompt-button-i.md) | Describes the menu item button in the action menu. |
| [ShowDialogOptions](arkts-arkui-prompt-showdialogoptions-i.md) | Describes the options for showing the dialog box. |
| [ShowDialogSuccessResponse](arkts-arkui-prompt-showdialogsuccessresponse-i.md) | Describes the dialog box response result. |
| [ShowToastOptions](arkts-arkui-prompt-showtoastoptions-i.md) | Describes the options for showing the toast. |
