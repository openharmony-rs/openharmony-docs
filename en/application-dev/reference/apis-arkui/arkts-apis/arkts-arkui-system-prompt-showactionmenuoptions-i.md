# ShowActionMenuOptions

```TypeScript
export interface ShowActionMenuOptions
```

Describes the options for showing the action menu.

**Since:** 6

<!--Device-unnamed-export interface ShowActionMenuOptions--><!--Device-unnamed-export interface ShowActionMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## complete

```TypeScript
complete?: () => void
```

Callback invoked when the API call is complete.

**Since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowActionMenuOptions-complete?: () => void--><!--Device-ShowActionMenuOptions-complete?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (errMsg: string) => void
```

Callback invoked upon failure.

**Since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowActionMenuOptions-fail?: (errMsg: string) => void--><!--Device-ShowActionMenuOptions-fail?: (errMsg: string) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errMsg | string | Yes |  |

## success

```TypeScript
success?: (tapIndex: number, errMsg: string) => void
```

Callback invoked when an action menu item is selected successfully.

**Since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowActionMenuOptions-success?: (tapIndex: number, errMsg: string) => void--><!--Device-ShowActionMenuOptions-success?: (tapIndex: number, errMsg: string) => void-End-->

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

Array of buttons in the action menu. The structure is {text: 'button', color: '#666666'}, which supports 1 to 6 buttons.

**Type:** [Button, Button?, Button?, Button?, Button?, Button?]

**Since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]--><!--Device-ShowActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

Title of the text to display.

**Type:** string

**Since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowActionMenuOptions-title?: string--><!--Device-ShowActionMenuOptions-title?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
