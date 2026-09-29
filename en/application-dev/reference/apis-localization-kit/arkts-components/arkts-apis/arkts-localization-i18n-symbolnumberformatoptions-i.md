# SymbolNumberFormatOptions

```TypeScript
export interface SymbolNumberFormatOptions extends Intl.NumberFormatOptions
```

Represents optional configuration items for the SymbolNumberFormat object. Define the symbol element and value that need to be replaced.

**Inheritance/Implementation:** SymbolNumberFormatOptions extends Intl.NumberFormatOptions

**Since:** 26.0.0

<!--Device-i18n-export interface SymbolNumberFormatOptions extends Intl.NumberFormatOptions--><!--Device-i18n-export interface SymbolNumberFormatOptions extends Intl.NumberFormatOptions-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## groupingSeparator

```TypeScript
groupingSeparator?: string | undefined
```

Grouping Separator symbol of localized number part, such as "," of "10,000".

**Type:** string &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SymbolNumberFormatOptions-groupingSeparator?: string | undefined--><!--Device-SymbolNumberFormatOptions-groupingSeparator?: string | undefined-End-->

**System capability:** SystemCapability.Global.I18n

## infinity

```TypeScript
infinity?: string | undefined
```

Infinity symbol of localized number part, such as "∞".

**Type:** string &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SymbolNumberFormatOptions-infinity?: string | undefined--><!--Device-SymbolNumberFormatOptions-infinity?: string | undefined-End-->

**System capability:** SystemCapability.Global.I18n

## minusSign

```TypeScript
minusSign?: string | undefined
```

Minus sign of localized number part, such as "-".

**Type:** string &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SymbolNumberFormatOptions-minusSign?: string | undefined--><!--Device-SymbolNumberFormatOptions-minusSign?: string | undefined-End-->

**System capability:** SystemCapability.Global.I18n

## nan

```TypeScript
nan?: string | undefined
```

NaN symbol of localized number part, such as "null".

**Type:** string &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SymbolNumberFormatOptions-nan?: string | undefined--><!--Device-SymbolNumberFormatOptions-nan?: string | undefined-End-->

**System capability:** SystemCapability.Global.I18n

## plusSign

```TypeScript
plusSign?: string | undefined
```

Plus sign of localized number part, such as "+".

**Type:** string &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SymbolNumberFormatOptions-plusSign?: string | undefined--><!--Device-SymbolNumberFormatOptions-plusSign?: string | undefined-End-->

**System capability:** SystemCapability.Global.I18n

## zero

```TypeScript
zero?: string | undefined
```

Zero symbol of localized number part, such as "0".

**Type:** string &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SymbolNumberFormatOptions-zero?: string | undefined--><!--Device-SymbolNumberFormatOptions-zero?: string | undefined-End-->

**System capability:** SystemCapability.Global.I18n
