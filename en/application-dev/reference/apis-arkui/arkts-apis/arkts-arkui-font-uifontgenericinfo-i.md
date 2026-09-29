# UIFontGenericInfo

```TypeScript
interface UIFontGenericInfo
```

Defines a list of supported generic font families.

**Since:** 11

<!--Device-font-interface UIFontGenericInfo--><!--Device-font-interface UIFontGenericInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## adjust

```TypeScript
adjust: Array<UIFontAdjustInfo>
```

Font weight value mapping list, which maps the original weight values of the fonts to the actually displayed weight values.

**Type:** Array&lt;[UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontGenericInfo-adjust: Array<UIFontAdjustInfo>--><!--Device-UIFontGenericInfo-adjust: Array<UIFontAdjustInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alias

```TypeScript
alias: Array<UIFontAliasInfo>
```

Alias list of the font family, used to provide alternative names for the fonts.

**Type:** Array&lt;[UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontGenericInfo-alias: Array<UIFontAliasInfo>--><!--Device-UIFontGenericInfo-alias: Array<UIFontAliasInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## family

```TypeScript
family: string
```

Font family name, which is the value of **family** specified in the font file.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIFontGenericInfo-family: string--><!--Device-UIFontGenericInfo-family: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
