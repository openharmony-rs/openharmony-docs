# UIFontAliasInfo

UI font configuration of the system.

**Since:** 11

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight: number
```

Weight of the fonts included in the font family. If the value is greater than 0, the font family contains only the fonts with the specified weight. If the value is 0, the font family contains all fonts.

Valid values are **0**, **100**, **400**, **700**, and **900**.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
