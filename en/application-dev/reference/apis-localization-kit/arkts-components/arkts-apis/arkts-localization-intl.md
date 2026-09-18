# @ohos.intl(Internationalization)

The **intl** module provides basic i18n capabilities, such as time and date formatting, number formatting, and string sorting, through the standard i18n APIs defined in ECMA 402.

**Since:** 6

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Collator](arkts-localization-intl-collator-c.md) | Provides the string collation capability. |
| [DateTimeFormat](arkts-localization-intl-datetimeformat-c.md) | Performs date and time formatting. |
| [Locale](arkts-localization-intl-locale-c.md) | Provides APIs for obtaining locale information. |
| [NumberFormat](arkts-localization-intl-numberformat-c.md) | Provides the API for formatting number strings. |
| [PluralRules](arkts-localization-intl-pluralrules-c.md) | Provides the capability for obtaining the plural rule type. |
| [RelativeTimeFormat](arkts-localization-intl-relativetimeformat-c.md) | Provides the relative time formatting capability. |

### Interfaces

| Name | Description |
| --- | --- |
| [CollatorOptions](arkts-localization-intl-collatoroptions-i.md) | Defines the options for creating a **Collator** object. Since API version 9, the attributes in **CollatorOptions** are optional. |
| [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | Defines the options for a **DateTimeOptions** object. Since API version 9, the **DateTimeOptions** attribute is changed from mandatory to optional. |
| [LocaleOptions](arkts-localization-intl-localeoptions-i.md) | Options for initializing the **Locale** object. Since API version 9, the **LocaleOptions** attribute is changed from mandatory to optional. |
| [NumberOptions](arkts-localization-intl-numberoptions-i.md) | Options for creating the **NumberFormat** object. Since API version 9, the **NumberOptions** attribute is changed from mandatory to optional. |
| [PluralRulesOptions](arkts-localization-intl-pluralrulesoptions-i.md) | Defines the options for creating a **PluralRules** object. Since API version 9, the **PluralRulesOptions** attribute is changed from mandatory to optional. |
| [RelativeTimeFormatInputOptions](arkts-localization-intl-relativetimeformatinputoptions-i.md) | Defines the configuration options for a **RelativeTimeFormat** object. Since API version 9, the attributes in **RelativeTimeFormatInputOptions** are optional. |
| [RelativeTimeFormatResolvedOptions](arkts-localization-intl-relativetimeformatresolvedoptions-i.md) | Represents the formatting options for the **RelativeTimeFormat** object. |
