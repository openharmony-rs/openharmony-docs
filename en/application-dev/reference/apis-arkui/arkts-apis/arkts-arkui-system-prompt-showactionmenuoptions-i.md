# ShowActionMenuOptions

Defines the option of ShowActionMenu.

@interface ShowActionMenuOptions

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## complete

```TypeScript
complete?: () => void
```

Called when the dialog box is closed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (errMsg: string) => void
```

Called when the operation is cancelled.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errMsg | string | Yes |  |

## success

```TypeScript
success?: (tapIndex: number, errMsg: string) => void
```

Called when the dialog box is displayed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tapIndex | number | Yes |  |
| errMsg | string | Yes |  |

## buttons

```TypeScript
buttons: [Button, Button?, Button?, Button?, Button?, Button?]
```

Array of buttons in the dialog box. The array structure is {text:'button', color: '#666666'}. One to six buttons are supported.

**Type:** [Button, Button?, Button?, Button?, Button?, Button?]

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

Title of the text to display.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
