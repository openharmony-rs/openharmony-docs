# LocaleItem (System API)

```TypeScript
export interface LocaleItem
```

Represents the locale information, which consists of the language, script, and country/region.

**Since:** 10

<!--Device-i18n-export interface LocaleItem--><!--Device-i18n-export interface LocaleItem-End-->

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## displayName

```TypeScript
displayName: string
```

Representation of ID in the specified locale in SystemLocaleManager.

**Type:** string

**Since:** 10

<!--Device-LocaleItem-displayName: string--><!--Device-LocaleItem-displayName: string-End-->

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## id

```TypeScript
id: string
```

Language code or country/region code, for example, "zh" or "CN".

**Type:** string

**Since:** 10

<!--Device-LocaleItem-id: string--><!--Device-LocaleItem-id: string-End-->

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## localName

```TypeScript
localName?: string
```

Local name of the ID.

**Type:** string

**Since:** 10

<!--Device-LocaleItem-localName?: string--><!--Device-LocaleItem-localName?: string-End-->

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## suggestionType

```TypeScript
suggestionType: SuggestionType
```

Language or country/region suggestion type.

**Type:** [SuggestionType](arkts-localization-i18n-suggestiontype-e-sys.md)

**Since:** 10

<!--Device-LocaleItem-suggestionType: SuggestionType--><!--Device-LocaleItem-suggestionType: SuggestionType-End-->

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.
