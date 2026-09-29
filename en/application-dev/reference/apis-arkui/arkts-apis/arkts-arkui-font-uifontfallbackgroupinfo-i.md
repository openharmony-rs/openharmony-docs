# UIFontFallbackGroupInfo

```TypeScript
interface UIFontFallbackGroupInfo
```

Defines a list of fallback generic font families.

**Since:** 11

<!--Device-font-interface UIFontFallbackGroupInfo--><!--Device-font-interface UIFontFallbackGroupInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## fallback

```TypeScript
fallback: Array<UIFontFallbackInfo>
```

Fallback fonts for the font family. If **fontSetName** is set to **""**, it indicates that the fonts can be used as fallback fonts for all font families.

**Type:** Array&lt;[UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontFallbackGroupInfo-fallback: Array<UIFontFallbackInfo>--><!--Device-UIFontFallbackGroupInfo-fallback: Array<UIFontFallbackInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSetName

```TypeScript
fontSetName: string
```

Name of the font family corresponding to the fallback font group. If **fontSetName** is set to **""**, the fallback font group can be used for all font families.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontFallbackGroupInfo-fontSetName: string--><!--Device-UIFontFallbackGroupInfo-fontSetName: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
