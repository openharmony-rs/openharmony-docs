# UIFontAdjustInfo

```TypeScript
interface UIFontAdjustInfo
```

Provides a mapping list between the original weight value of a font and the actual displayed weight value.

**Since:** 11

<!--Device-font-interface UIFontAdjustInfo--><!--Device-font-interface UIFontAdjustInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## to

```TypeScript
to: number
```

Weight value of the font displayed in the application.

The value options can be **100**, **400**, **700**, and **900**.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontAdjustInfo-to: number--><!--Device-UIFontAdjustInfo-to: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight: number
```

Original weight value of the font.

The value options can be **50**, **80**, **100**, and **200**.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontAdjustInfo-weight: number--><!--Device-UIFontAdjustInfo-weight: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
