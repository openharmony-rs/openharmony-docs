# BilingualIndexMode

```TypeScript
export enum BilingualIndexMode
```

Enumerates bilingual index modes, which determine the combination of local index and English index.

**Since:** 26.2.0

<!--Device-i18n-export enum BilingualIndexMode--><!--Device-i18n-export enum BilingualIndexMode-End-->

**System capability:** SystemCapability.Global.I18n

## COMPRESSED_EN

```TypeScript
COMPRESSED_EN = 1
```

Compressed English list: local index + English index compressed to 'Z'.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-BilingualIndexMode-COMPRESSED_EN = 1--><!--Device-BilingualIndexMode-COMPRESSED_EN = 1-End-->

**System capability:** SystemCapability.Global.I18n

## COMPRESSED_LOCAL

```TypeScript
COMPRESSED_LOCAL = 2
```

Compressed local list: local index first letter + English index.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-BilingualIndexMode-COMPRESSED_LOCAL = 2--><!--Device-BilingualIndexMode-COMPRESSED_LOCAL = 2-End-->

**System capability:** SystemCapability.Global.I18n

## FULL

```TypeScript
FULL = 0
```

Full list: local index + English index.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-BilingualIndexMode-FULL = 0--><!--Device-BilingualIndexMode-FULL = 0-End-->

**System capability:** SystemCapability.Global.I18n
