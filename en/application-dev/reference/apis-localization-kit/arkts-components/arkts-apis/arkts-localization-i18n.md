# @ohos.i18n(Internationalization)

This module provides system-related and enhanced [i18n](../../../internationalization/i18n-l10n.md) capabilities, such as locale management, phone number formatting, and calendar, through supplementary i18n APIs that are not defined in [ECMA 402](https://dev.ecma-international.org/publications-and-standards/standards/ecma-402/). The [intl](arkts-localization-intl.md) module provides basic i18n capabilities through the standard i18n APIs defined in ECMA
402. It works with the **i18n** module to provide a complete suite of i18n capabilities. The terms used in the APIs
are defined as follows:

- Pattern string, which is a string consisting of [Unicode date field symbols](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table) and custom text enclosed by single quotation marks.  
- Skeleton string: a string that consists of [Unicode date field symbols](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table) and does not support custom text.

> **NOTE:** 
> 
> - The APIs of this module are based on the [CLDR](https://cldr.unicode.org) internationalization database. The processing results of the APIs may be adjusted as the CLDR standard evolves. For example, the return value of the [date and time formatting API](arkts-localization-i18n-simplenumberformat-c.md) is used only for UI display. Do not hardcode the return value or make assumptions about the return value. Otherwise, version compatibility problems may occur. API version 12 corresponds to [CLDR 42](https://cldr.unicode.org/index/downloads/cldr-42). For details about data changes, see the official CLDR documentation.
> 
> - Since API version 11, some APIs of this module are supported in ArkTS widgets.

**Since:** 7

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addPreferredLanguage](arkts-localization-i18n-addpreferredlanguage-f.md) | Adds a preferred language to the specified position on the preferred language list. |
| [getCalendar](arkts-localization-i18n-getcalendar-f.md) | Obtains the **Calendar** object for the specified locale and calendar type. |
| [getChineseCalendar](arkts-localization-i18n-getchinesecalendar-f.md) | Obtains the ChineseCalendar object for the specified locale. |
| [getDisplayCountry](arkts-localization-i18n-getdisplaycountry-f.md) | Obtains the localized name of the specified country/region. |
| [getDisplayLanguage](arkts-localization-i18n-getdisplaylanguage-f.md) | Obtains the localized script for the specified language. |
| [getFirstPreferredLanguage](arkts-localization-i18n-getfirstpreferredlanguage-f.md) | Obtains the first language in the preferred language list. |
| [getInstance](arkts-localization-i18n-getinstance-f.md) | Creates an **IndexUtil** object. |
| [getLineInstance](arkts-localization-i18n-getlineinstance-f.md) | Obtains a **BreakIterator** object. The **BreakIterator** object maintains an internal break iterator that can be used to access various line break points. |
| [getPreferredLanguageList](arkts-localization-i18n-getpreferredlanguagelist-f.md) | Obtains the list of preferred languages. |
| [getSimpleDateTimeFormatByPattern](arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md) | Obtains a **SimpleDateTimeFormat** object based on the specified pattern string. For details about the difference between the objects obtained by this API and [getSimpleDateTimeFormatBySkeleton](arkts-localization-i18n-getsimpledatetimeformatbyskeleton-f.md), see the examples in [SimpleDateTimeFormat.format](arkts-localization-i18n-simpledatetimeformat-c.md#format). |
| [getSimpleDateTimeFormatByPattern](arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md) | Obtains a **SimpleDateTimeFormat** object based on the specified pattern string. For details about the difference between the objects obtained by this API and [getSimpleDateTimeFormatBySkeleton](arkts-localization-i18n-getsimpledatetimeformatbyskeleton-f.md), see the examples in [SimpleDateTimeFormat.format](arkts-localization-i18n-simpledatetimeformat-c.md#format). |
| [getSimpleDateTimeFormatBySkeleton](arkts-localization-i18n-getsimpledatetimeformatbyskeleton-f.md) | Obtains a **SimpleDateTimeFormat** object based on the specified skeleton. For details about the difference between the objects obtained by this API and [getSimpleDateTimeFormatByPattern](arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md), see the examples in [SimpleDateTimeFormat.format](arkts-localization-i18n-simpledatetimeformat-c.md#format). |
| [getSimpleDateTimeFormatBySkeleton](arkts-localization-i18n-getsimpledatetimeformatbyskeleton-f.md) | Obtains a **SimpleDateTimeFormat** object based on the specified skeleton. For details about the difference between the objects obtained by this API and [getSimpleDateTimeFormatByPattern](arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md), see the examples in [SimpleDateTimeFormat.format](arkts-localization-i18n-simpledatetimeformat-c.md#format). |
| [getSimpleNumberFormatBySkeleton](arkts-localization-i18n-getsimplenumberformatbyskeleton-f.md) | Obtains a **SimpleNumberFormat** object based on the specified skeleton. |
| [getSimpleNumberFormatBySkeleton](arkts-localization-i18n-getsimplenumberformatbyskeleton-f.md) | Obtains a **SimpleNumberFormat** object based on the specified skeleton. |
| [getSystemLanguage](arkts-localization-i18n-getsystemlanguage-f.md) | Obtains the system language. |
| [getSystemLocale](arkts-localization-i18n-getsystemlocale-f.md) | Obtains the system locale. |
| [getSystemRegion](arkts-localization-i18n-getsystemregion-f.md) | Obtains the system region. |
| [getTimeZone](arkts-localization-i18n-gettimezone-f.md) | Obtains the **TimeZone** object corresponding to the specified time zone ID. |
| [is24HourClock](arkts-localization-i18n-is24hourclock-f.md) | Checks whether the 24-hour clock is used. |
| [isRTL](arkts-localization-i18n-isrtl-f.md) | Checks whether a language is an RTL language. For an RTL language, [UI mirroring](../../../internationalization/i18n-ui-design.md#ui-mirroring) is required. |
| [removePreferredLanguage](arkts-localization-i18n-removepreferredlanguage-f.md) | Removes a preferred language from the specified position on the preferred language list. |
| [set24HourClock](arkts-localization-i18n-set24hourclock-f.md) | Sets the 24-hour clock. |

### Classes

| Name | Description |
| --- | --- |
| [AdvancedMeasureFormat](arkts-localization-i18n-advancedmeasureformat-c.md) | Provides the number formatting capability, supporting automatic unit conversion based on specific application scenarios. |
| [BreakIterator](arkts-localization-i18n-breakiterator-c.md) | Provides text line breaking capabilities, such as obtaining, moving, and identifying break points. |
| [Calendar](arkts-localization-i18n-calendar-c.md) | Provides calendar management capabilities, such as calendar name retrieval and date calculation. |
| [Character](arkts-localization-i18n-character-c.md) | Provides the API for accessing unicode character properties. For example, determine whether a character is a number. |
| [ChineseCalendar](arkts-localization-i18n-chinesecalendar-c.md) | Provide a ChineseCalendar interface which could handle unique characteristics of the chinese calendar, such as leap month. |
| [EntityRecognizer](arkts-localization-i18n-entityrecognizer-c.md) | Provides entity recognition capabilities, which can be used to obtain the type and start and end positions of an entity in the text. Currently, supported entities include phone numbers, and date and time. |
| [HolidayManager](arkts-localization-i18n-holidaymanager-c.md) | Provides holiday data parsing capabilities, such as determining holidays and obtaining the holiday list of a specified year. |
| [I18NUtil](arkts-localization-i18n-i18nutil-c.md) | Internationalization utility class, which provides the capabilities of unit conversion, date sequence retrieval, time segment name retrieval, region matching, and path localization. |
| [IndexUtil](arkts-localization-i18n-indexutil-c.md) | Provides index management capabilities, such as obtaining the locale index list and text index values. |
| [ISO8601DateTimeFormat](arkts-localization-i18n-iso8601datetimeformat-c.md) | Provide a DateTime formatting interface which could format date to ISO 8601 standard string. [ISO8601](https://iso8601.com/). |
| [Normalizer](arkts-localization-i18n-normalizer-c.md) | Provides the text normalization capabilities. |
| [PhoneNumberFormat](arkts-localization-i18n-phonenumberformat-c.md) | Provides phone number management capabilities, such as phone number validity verification, formatting, and home location retrieval. |
| [SimpleDateTimeFormat](arkts-localization-i18n-simpledatetimeformat-c.md) | Provide a simple date time formatting interface. |
| [SimpleNumberFormat](arkts-localization-i18n-simplenumberformat-c.md) | Formats a number based on the specified skeleton string. |
| [StyledDateTimeFormat](arkts-localization-i18n-styleddatetimeformat-c.md) | Provide a DateTime formatting interface which could format DateTime to StyleString. |
| [StyledNumberFormat](arkts-localization-i18n-stylednumberformat-c.md) | Provide a number formatting interface which could format number to StyleString. |
| [SymbolDateTimeFormat](arkts-localization-i18n-symboldatetimeformat-c.md) | Provide a DateTime formatting interface that supports custom symbols. This interface formats date time values into strings with custom symbols, and can replace variable symbols in the formatted result with custom fixed symbols (e.g., replacing "2:23 PM" with "2:23 afternoon"). |
| [SymbolNumberFormat](arkts-localization-i18n-symbolnumberformat-c.md) | Provide a Number formatting interface that supports custom symbols. This interface formats number values into strings with custom symbols, and can replace variable symbols in the formatted result with custom fixed symbols (e.g., replacing "null" to "NA"). |
| [System](arkts-localization-i18n-system-c.md) | Provides system attribute configuration functions, including translating language and country/region names, obtaining the list of supported languages and countries/regions, and obtaining the system language and region. |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | Provides time zone management capabilities, such as time zone name translation, offset retrieval, and transition rule retrieval. |
| [Transliterator](arkts-localization-i18n-transliterator-c.md) | Provides text transliteration capabilities, such as obtaining the supported language IDs and transliterating text. |
| [Unicode](arkts-localization-i18n-unicode-c.md) | Provides character attribute management capabilities, such as checking whether a character is a space, digit, or letter. |
| [ZoneOffsetTransition](arkts-localization-i18n-zoneoffsettransition-c.md) | Provides the API for obtaining a timezone transition information. |
| [ZoneRules](arkts-localization-i18n-zonerules-c.md) | Queries the time zone transition rule. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [System](arkts-localization-i18n-system-c-sys.md) | Provides system attribute configuration functions, including translating language and country/region names, obtaining the list of supported languages and countries/regions, and obtaining the system language and region. |
| [SystemLocaleManager](arkts-localization-i18n-systemlocalemanager-c-sys.md) | Provide some functions for settings and startup guide to select language or region. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AdvancedMeasureFormatOptions](arkts-localization-i18n-advancedmeasureformatoptions-i.md) | Represents optional configuration items for AdvancedMeasureFormat object. |
| [ChineseCalendarTime](arkts-localization-i18n-chinesecalendartime-i.md) | Represents chinese calendar time element for the ChineseCalendar object. |
| [EncodingInfo](arkts-localization-i18n-encodinginfo-i.md) | Defines the detect encoding result information. |
| [EntityInfoItem](arkts-localization-i18n-entityinfoitem-i.md) | Defines a list of entities. |
| [HolidayInfoItem](arkts-localization-i18n-holidayinfoitem-i.md) | Represents the holiday information. |
| [HolidayLocalName](arkts-localization-i18n-holidaylocalname-i.md) | Represents the name of a holiday in different languages. |
| [ISO8601DateTimeFormatOptions](arkts-localization-i18n-iso8601datetimeformatoptions-i.md) | Represents optional configuration items for the ISO8601DateTimeFormat object. These options determine which elements need to be displayed after formatting and the corresponding format. |
| [PhoneNumberFormatOptions](arkts-localization-i18n-phonenumberformatoptions-i.md) | Options for **PhoneNumberFormat** object initialization. |
| [ResolvedSymbolDateTimeFormatOptions](arkts-localization-i18n-resolvedsymboldatetimeformatoptions-i.md) | Represents optional element for the ResolvedSymbolDateTimeFormatOptions object. Define the resolved symbol element and value that need to get. |
| [ResolvedSymbolNumberFormatOptions](arkts-localization-i18n-resolvedsymbolnumberformatoptions-i.md) | Represents optional element for the ResolvedSymbolNumberFormatOptions object. Define the resolved symbol element and value that need to get. |
| [StyledDateTimeFormatOptions](arkts-localization-i18n-styleddatetimeformatoptions-i.md) | Optional configuration items for creating the time and date formatting object for rich text display. |
| [StyledNumberFormatOptions](arkts-localization-i18n-stylednumberformatoptions-i.md) | Represents optional configuration items for the **NumberFormat** object. |
| [SymbolDateTimeFormatOptions](arkts-localization-i18n-symboldatetimeformatoptions-i.md) | Represents optional configuration items for the SymbolDateTimeFormat object. Define the symbol element and value that need to be replaced. |
| [SymbolNumberFormatOptions](arkts-localization-i18n-symbolnumberformatoptions-i.md) | Represents optional configuration items for the SymbolNumberFormat object. Define the symbol element and value that need to be replaced. |
| [UnitInfo](arkts-localization-i18n-unitinfo-i.md) | Defines the measurement unit information. |
| [Util](arkts-localization-i18n-util-i.md) | Provides util functions. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [LocaleItem](arkts-localization-i18n-localeitem-i-sys.md) | Represents the locale information, which consists of the language, script, and country/region. |
| [SortOptions](arkts-localization-i18n-sortoptions-i-sys.md) | Represents the language or country/region sorting option. |
| [TimeZoneCityItem](arkts-localization-i18n-timezonecityitem-i-sys.md) | Represents a time zone and city combination item. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [NormalizerMode](arkts-localization-i18n-normalizermode-e.md) | Enumerates text normalization modes. |
| [TemperatureType](arkts-localization-i18n-temperaturetype-e.md) | Enumerates temperature units. |
| [UnitUsage](arkts-localization-i18n-unitusage-e.md) | Enumerates unit formatting scenarios. |
| [WeekDay](arkts-localization-i18n-weekday-e.md) | Enumerates the first day of a week. The value ranges from Monday to Sunday. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [SuggestionType](arkts-localization-i18n-suggestiontype-e-sys.md) | Represents the language or country/region suggestion type. |
<!--DelEnd-->
