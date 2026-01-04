# 全球化子系统Changelog

## cl.global.1 ICU版本升级

**访问级别**

公开接口

**变更原因**

ICU 版本由72.1升级至74.2，使时间、数字等格式化结果，以及分词换行结果发生变化。

**变更影响**

此变更不涉及应用适配。

| 变更前 | 变更后 |
| --- | --- |
| 时间、数字等格式化结果基于ICU 72.1版本，例如：繁体中文日期显示为“2024年4月23日”；英文日期范围显示为“20/12/2020 – 21/12/2020”。 | 时间、数字等格式化结果基于ICU 74.2版本，例如：繁体中文日期显示为“2024 年 4 月 23 日”；英文日期范围显示为“20/12/2020 – 21/12/2020”。|
| 对于中日韩表意字符，以U+31EF为例，升级前，在U+31EF字符前换行。 | 新增627个中日韩表意字符；升级后，在U+31EF字符后换行。 |
| 缅甸语、泰语、老挝语、高棉语使用ICU 72.1的换行规则，例如文本“သော့换行点ခလောက်”在“换行点”处断开。 | 优化缅甸语、泰语、老挝语、高棉语的换行规则，支持在正字法音节间断行，例如文本“换行点သော့ခလောက်”在“换行点”处断开。 |
| @ 符号会与相邻字母粘连，例如“service@baidu.com”被识别为一个不可分割的整体。 | @ 符号两侧会被识别为单词边界，例如“service@baidu.com”会被识别为“service”、“@”、“baidu.com”三个部分。 |

**起始API Level**

API 6

**变更发生版本**

从OpenHarmony SDK 6.1.0.21开始。

**变更的接口/组件**

[intl.DateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated)

[intl.DateTimeFormat.formatRange](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatrangedeprecated)

[intl.Locale.maximize](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#maximizedeprecated)

[intl.Locale.minimize](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#minimizedeprecated)

[intl.RelativeTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated-1)

[i18n.System.getDisplayCountry](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplaycountry9)

[i18n.System.getDisplayLanguage](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplaylanguage9)

[i18n.Transliterator.transform](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#transform9)

[i18n.TimeZone.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname)

[i18n.Calendar.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname8)

[i18n.StyledDateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#format23)

[i18n.SimpleDateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#format18)

[Date.toLocaleDateString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleDateString)

[Date.toLocaleString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString)

[Date.toLocaleTimeString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleTimeString)

[Intl.DateTimeFormat.format](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/format)

[Intl.DateTimeFormat.formatRange](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/formatRange)

[Intl.DateTimeFormat.formatRangeToParts](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/formatRangeToParts)

[Intl.ListFormat.format](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/format)

[Intl.RelativeTimeFormat.format](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/format)

[Intl.Locale.maximize](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/maximize)

[Intl.Locale.minimize](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale/minimize)

**适配指导**

接口默认效果变更，但开发者需审视此变更是否对自身相关业务展示效果产生影响，若有影响需根据自身业务代码进行对应适配。
