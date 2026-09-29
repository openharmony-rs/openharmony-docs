# ShowToastOptions

```TypeScript
export interface ShowToastOptions
```

Describes the options for showing the toast.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md)

<!--Device-unnamed-export interface ShowToastOptions--><!--Device-unnamed-export interface ShowToastOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom?: string | number
```

Distance between the toast border and the bottom of the screen.

**Type:** string &#124; number

**Since:** 5

**Deprecated since:** 8

**Substitutes:** [bottom](arkts-arkui-promptaction-showtoastoptions-i.md#bottom)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ShowToastOptions-bottom?: string | number--><!--Device-ShowToastOptions-bottom?: string | number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Duration that the toast will remain on the screen. The default value is 1500 ms. The recommended value range is 1500 ms to 10000 ms. If a value less than 1500 ms is set, the default value is used.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [duration](arkts-arkui-promptaction-showtoastoptions-i.md#duration)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ShowToastOptions-duration?: number--><!--Device-ShowToastOptions-duration?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

Text to display.

**Type:** string

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [message](arkts-arkui-promptaction-showtoastoptions-i.md#message)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ShowToastOptions-message: string--><!--Device-ShowToastOptions-message: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
