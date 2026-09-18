# LocaleItem (System API)

Represents the locale information, which consists of the language, script, and country/region.

**Since:** 10

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

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## id

```TypeScript
id: string
```

Language code or country/region code, for example, "zh" or "CN".

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## localName

```TypeScript
localName?: string
```

Local name of the ID.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## suggestionType

```TypeScript
suggestionType: SuggestionType
```

Language or country/region suggestion type.

**Type:** [SuggestionType](arkts-localization-i18n-suggestiontype-e-sys.md)

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.
