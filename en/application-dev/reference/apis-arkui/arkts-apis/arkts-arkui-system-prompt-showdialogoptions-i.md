# ShowDialogOptions

```TypeScript
export interface ShowDialogOptions
```

Describes the options for showing the dialog box.

**Since:** 3

<!--Device-unnamed-export interface ShowDialogOptions--><!--Device-unnamed-export interface ShowDialogOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (data: string, code: string) => void
```

Callback invoked when the API call is canceled.

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowDialogOptions-cancel?: (data: string, code: string) => void--><!--Device-ShowDialogOptions-cancel?: (data: string, code: string) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | string | Yes |  |

## complete

```TypeScript
complete?: (data: string) => void
```

Called invoked when the API call is complete.

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowDialogOptions-complete?: (data: string) => void--><!--Device-ShowDialogOptions-complete?: (data: string) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |

## success

```TypeScript
success?: (data: ShowDialogSuccessResponse) => void
```

Callback invoked upon success.

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowDialogOptions-success?: (data: ShowDialogSuccessResponse) => void--><!--Device-ShowDialogOptions-success?: (data: ShowDialogSuccessResponse) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [ShowDialogSuccessResponse](arkts-arkui-system-prompt-showdialogsuccessresponse-i.md) | Yes |  |

## buttons

```TypeScript
buttons?: [Button, Button?, Button?]
```

Array of buttons in the dialog box. The structure is {text:'button', color: '#666666'}, which supports 1 to 3 buttons. If more than 3 buttons are specified, the dialog box is not displayed.

**Type:** [Button, Button?, Button?]

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowDialogOptions-buttons?: [Button, Button?, Button?]--><!--Device-ShowDialogOptions-buttons?: [Button, Button?, Button?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: string
```

Text body.

**Type:** string

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowDialogOptions-message?: string--><!--Device-ShowDialogOptions-message?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

Title of the text to display.

**Type:** string

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShowDialogOptions-title?: string--><!--Device-ShowDialogOptions-title?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
