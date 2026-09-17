# Prompt

Defines the prompt interface.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## showActionMenu

```TypeScript
static showActionMenu(options: ShowActionMenuOptions): void
```

Displays the menu.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowActionMenuOptions](arkts-arkui-system-prompt-showactionmenuoptions-i.md) | Yes | Options. |

## showDialog

```TypeScript
static showDialog(options: ShowDialogOptions): void
```

Displays the dialog box.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowDialogOptions](arkts-arkui-system-prompt-showdialogoptions-i.md) | Yes | Options. |

## showToast

```TypeScript
static showToast(options: ShowToastOptions): void
```

Displays the notification text.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-system-prompt-showtoastoptions-i.md) | Yes | Options. |
