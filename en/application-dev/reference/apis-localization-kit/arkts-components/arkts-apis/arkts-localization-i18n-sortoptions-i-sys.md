# SortOptions (System API)

Represents the language or country/region sorting option.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## isSuggestedFirst

```TypeScript
isSuggestedFirst?: boolean
```

Whether to move the recommended language or country/region to the top in the sorting result. The value "true"means to move the recommended language or country/region to the top, and the value "false" means the opposite. The default value is true.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## isUseLocalName

```TypeScript
isUseLocalName?: boolean
```

Whether to use the local name for sorting. The value "true" means to use the local name for sorting, and the value "false" means the opposite. If getLanguageInfoArray is called, the default value of isUseLocalName is true. If getRegionInfoArray is called, the default value of isUseLocalName is false.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.

## locale

```TypeScript
locale?: string
```

Locale information, which consists of the language, script, and country/region, for example, "zh-Hans-CN". The default value is the current system locale.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Global.I18n

**System API:** This is a system API.
