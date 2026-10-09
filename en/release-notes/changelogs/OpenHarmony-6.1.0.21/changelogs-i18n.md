# Globalization Subsystem Changelog

## cl.global.1 Enhancements to Localization Display and Line Breaking in Globalization and Runtime APIs

**Access Level**

Public

**Reason for Change**

The ICU version has been upgraded from 72.1 to 74.2. Based on the [ICU 74.2 data](https://icu.unicode.org/download/74), this update improves localization conventions, making the behavior of certain globalization and runtime APIs better aligned with regional language usage. It also enhances the system's text line-breaking capabilities.

**Change Impact**

This change requires application adaptation.

For detailed API behavior changes, see **Affected APIs/Components**. Updates to system line-breaking behavior are as follows:

| Before| After|
| --- | --- |
|  CJK ideographs did not include characters in the range U+2EBF0 to U+2EE5F. | 622 ideographs and 5 special ideographic characters in this range are now included in CJK ideographs.|
| Line breaking between orthographic syllables was not supported for Burmese, Thai, Lao, and Khmer. For example, in a Text component, the Burmese text "သော့line-breaking pointခလောက်" would break at "line-breaking point".| Line breaking between orthographic syllables is now supported for Burmese, Thai, Lao, and Khmer. For example, in a Text component, the Burmese text "line-breaking pointသော့ခလောက်" breaks at "line-breaking point".|

**Starting API Level**

API 6

**Effective Version**

OpenHarmony SDK 6.1.0.21

**Affected APIs/Components**

| API | Example Scenario| Return Value (Before)| Return Value (After)|
| ---  | --- | --- | --- |
| [intl.DateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated) | Formatting April 23, 2024 in Traditional Chinese| 2024年4月23日 | 2024 年 4 月 23 日 |
| [intl.DateTimeFormat.formatRange](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatrangedeprecated) | Formatting December 20–21, 2020 in British English| 20/12/2020 – 21/12/2020 | 20/12/2020 – 21/12/2020 (separator updated)|
| [intl.Locale.maximize](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#maximizedeprecated) | Locale ID hy-arevmda| hyw | hyw-Armn-AM |
| [intl.Locale.minimize](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#minimizedeprecated) | Locale ID und-150| ru | en-150 |
| [intl.RelativeTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated-1) | Displaying "within 1 quarter" in English| in 1 qtr. | in 1q  |
| [i18n.System.getDisplayCountry](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplaycountry9) | Locale AC with language es| Isla de la Ascensión | Isla Ascensión |
| [i18n.System.getDisplayLanguage](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplaylanguage9) | Displaying language ID yue in Chinese| 粤文 | 粤语 |
| [i18n.Transliterator.transform](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#transform9) | Transliterate 𚽇 to Latin| 𚽇 | kē |
| [i18n.TimeZone.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname) | Display name of Asia/Kamchatka in Czech| Petropavlovsko-kamčatský standardní čas | petropavlovsko-kamčatský standardní čas |
| [i18n.Calendar.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname8) | Calendar type islamic_tbla in Chinese| 伊斯兰天文历 | islamic-tbla |
| [i18n.StyledDateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#format23) | Formatting Nov 1, 2025 16:14:06| Saturday, 1 November 2025, 16:14:06 Central Standard Time | Saturday 1 November 2025 at 16:14:06 Central Standard Time |
| [i18n.getSimpleDateTimeFormatBySkeleton](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#i18ngetsimpledatetimeformatbyskeleton20) | Formatting with skeleton yMdhms in Chinese| 13/12/2024 上午6:30:25 | 13/12/2024 上午 6:30:25 |
| Date.toLocaleDateString | Formatting date in Arabic| 'الخميس، ٢٠ ديسمبر ٢٠١٢'  |'الخميس، ٢٠ ديسمبر، ٢٠١٢' |
| Date.toLocaleString | Formatting date in English| 10/20/2022, 6:00:00 PM | 10/20/2022, 6:00:00 PM (space before PM updated)|
| Date.toLocaleTimeString | Formatting date in English| 6:00:00 PM | 6:00:00 PM (space before PM updated)|
| Intl.DateTimeFormat.format | Formatting April 23, 2024 in Traditional Chinese| 2024年4月23日 | 2024 年 4 月 23 日 |
| Intl.DateTimeFormat.formatRange | Formatting December 20–21, 2020 in British English| 20/12/2020 – 21/12/2020 | 20/12/2020 – 21/12/2020 (separator updated)|
| Intl.DateTimeFormat.formatRangeToParts | Formatting December 20–21, 2020 in English| { type: "literal", value: " – " } | {"type":"literal","value":" – "} (whitespace character in value updated)|
| Intl.ListFormat.format | Formatting list in Chinese| Motorcycle、Bus和Car | Motorcycle、Bus、Car |
| Intl.RelativeTimeFormat.format | Displaying "within 1 quarter" in English| in 1 qtr. | in 1q  |
| Intl.Locale.maximize | Locale ID hy-arevmda| hyw | hyw-Armn-AM |
| Intl.Locale.minimize | Locale ID und-150| ru | en-150 |
| [ubrk_next](../../../application-dev/reference/native-lib/icu4c-symbol.md) | Tokenizing "service@baidu.com"| The @ symbol is attached to adjacent letters, treated as a single token.| The @ symbol is treated as a word boundary, resulting in "service", "@", and "baidu.com".|

**Adaptation Guide**

This change updates the default behavior of APIs. You need to assess whether it affects your UI or display logic and update the code as needed.
<!--no_check-->