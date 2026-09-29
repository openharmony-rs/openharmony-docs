# UIFontFallbackInfo

```TypeScript
interface UIFontFallbackInfo
```

Provides the fallback font of the font set.

**Since:** 11

<!--Device-font-interface UIFontFallbackInfo--><!--Device-font-interface UIFontFallbackInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## family

```TypeScript
family: string
```

Font family name, which is the value of **family** specified in the font file.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontFallbackInfo-family: string--><!--Device-UIFontFallbackInfo-family: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## language

```TypeScript
language: string
```

Language type supported by the font family. The language format is a BCP47 tag (for example, **"zh-Hans"** indicates Simplified Chinese, and **"en"** indicates English).

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontFallbackInfo-language: string--><!--Device-UIFontFallbackInfo-language: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
