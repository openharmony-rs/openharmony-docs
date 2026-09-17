# ShowToastOptions

Defines the options of ShowToast.

@interface ShowToastOptions

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom?: string | number
```

The distance between toast dialog box and the bottom of screen.

**Type:** string &#124; number

**Since:** 5

**Deprecated since:** 8

**Substitutes:** [bottom](arkts-arkui-promptaction-showtoastoptions-i.md#bottom)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Duration of toast dialog box. The default value is 1500. The recommended value ranges from 1500 ms to 10000ms. NOTE: A value less than 1500 is automatically changed to 1500. The maximum value is 10000 ms.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [duration](arkts-arkui-promptaction-showtoastoptions-i.md#duration)

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
