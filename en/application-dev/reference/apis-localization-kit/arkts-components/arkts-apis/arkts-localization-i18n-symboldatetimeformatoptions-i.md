# SymbolDateTimeFormatOptions

Represents optional configuration items for the SymbolDateTimeFormat object. Define the symbol element and value that need to be replaced.

**Inheritance/Implementation:** SymbolDateTimeFormatOptions extends Intl.DateTimeFormatOptions

**Since:** 26.0.0

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## amPMSymbol

```TypeScript
amPMSymbol?: string[] | undefined
```

AM and PM symbol of date time period part, such as "PM" of "2:23 PM". The parameter array must be greater than 2, If greater than 2, the first two will be selected.

**Type:** string[] &#124; undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n
