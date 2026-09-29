# UIFontAliasInfo

```TypeScript
interface UIFontAliasInfo
```

Defines font alias configuration information.

**Since:** 11

<!--Device-font-interface UIFontAliasInfo--><!--Device-font-interface UIFontAliasInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## name

```TypeScript
name: string
```

Alias name.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontAliasInfo-name: string--><!--Device-UIFontAliasInfo-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight: number
```

When the value of **weight** is greater than 0, this font family contains only fonts of the specified weight. When the value of **weight** is 0, this font family contains all fonts.

The value options can be **0**, **100**, **400**, **700**, and **900**.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontAliasInfo-weight: number--><!--Device-UIFontAliasInfo-weight: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
