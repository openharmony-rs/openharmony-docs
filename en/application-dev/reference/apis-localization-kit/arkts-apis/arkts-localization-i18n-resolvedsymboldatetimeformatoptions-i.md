# ResolvedSymbolDateTimeFormatOptions

Represents optional element for the ResolvedSymbolDateTimeFormatOptions object. Define the resolved symbol element and value that need to get.

**Inheritance/Implementation:** ResolvedSymbolDateTimeFormatOptions extends Intl.ResolvedDateTimeFormatOptions

**Since:** 26.0.0

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## amPMSymbol

```TypeScript
amPMSymbol?: string[]
```

AM and PM symbol of date time period part, such as "PM" of "2:23 PM". First parameter is AM, second parameter is PM.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n
