# 全球化子系统Changelog

## cl.global.1 全球化接口与运行时接口本地化显示优化及换行能力增强

**访问级别**

公共能力

**变更原因**

ICU版本已从72.1升级至74.2，本次升级基于[ICU 74.2数据](https://icu.unicode.org/download/74)，优化了本地化表达习惯，使部分全球化接口及运行时接口的行为更贴合各地区的语言使用规范，同时提升了系统的文本换行处理能力。

**变更影响**

此变更涉及应用适配。

具体接口行为变化详见**变更的接口/组件**，系统换行能力更新如下：

| 变更前 | 变更后 |
| --- | --- |
|  中日韩表意字符未包含 U+2EBF0 至 U+2EE5F 范围内的字符。  | 中日韩表意字符新增该范围内 622 个表意字符及 5 个具有特殊含义的表意字符。 |
| 缅甸语、泰语、老挝语、高棉语不支持正字法音节之间进行断行处理，例如在Text控件中，缅甸语文本“သော့换行点ခလောက်”会在“换行点”处断开。 | 缅甸语、泰语、老挝语、高棉语支持正字法音节之间进行断行处理，例如在Text控件中，缅甸语文本“换行点သော့ခလောက်”会在“换行点”处断开。 |

**起始API Level**

API 6

**变更发生版本**

从OpenHarmony SDK 6.1.0.21开始。

**变更的接口/组件**

| 接口  | 变更场景举例 | 变更前返回值 | 变更后返回值 |
| ---  | --- | --- | --- |
| [intl.DateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated) | 繁体中文下格式化2024年4月23日 | 2024年4月23日 | 2024 年 4 月 23 日 |
| [intl.DateTimeFormat.formatRange](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatrangedeprecated) | 英式英语下格式化2020年12月20日至21日 | 20/12/2020 – 21/12/2020 | 20/12/2020 – 21/12/2020 （日期间连接符变更） |
| [intl.Locale.maximize](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#maximizedeprecated) | 区域ID为hy-arevmda | hyw | hyw-Armn-AM |
| [intl.Locale.minimize](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#minimizedeprecated) | 区域ID为und-150 | ru | en-150 |
| [intl.RelativeTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-intl.md#formatdeprecated-1) | 英文下显示在1季度内 | in 1 qtr. | in 1q  |
| [i18n.System.getDisplayCountry](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplaycountry9) | 地区ID是AC，语言ID是es | Isla de la Ascensión | Isla Ascensión |
| [i18n.System.getDisplayLanguage](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplaylanguage9) | 中文下显示语言ID为yue的名称 | 粤文 | 粤语 |
| [i18n.Transliterator.transform](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#transform9) | 将𪽇转换为拉丁文 | 𪽇 | kē |
| [i18n.TimeZone.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname) | Asia/Kamchatka时区在捷克语下的显示名称 | Petropavlovsko-kamčatský standardní čas | petropavlovsko-kamčatský standardní čas |
| [i18n.Calendar.getDisplayName](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#getdisplayname8) | type参数为islamic_tbla的历法在中文下的显示名称 | 伊斯兰天文历 | islamic-tbla |
| [i18n.StyledDateTimeFormat.format](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#format23) | 格式化2025年11月1日16:14:06 | Saturday, 1 November 2025, 16:14:06 Central Standard Time | Saturday 1 November 2025 at 16:14:06 Central Standard Time |
| [i18n.getSimpleDateTimeFormatBySkeleton](../../../application-dev/reference/apis-localization-kit/js-apis-i18n.md#i18ngetsimpledatetimeformatbyskeleton20) | 框架字符串传入yMdhms在中文下格式化日期 | 13/12/2024 上午6:30:25 | 13/12/2024 上午 6:30:25 |
| Date.toLocaleDateString | 在阿拉伯语下格式化日期| 'الخميس، ٢٠ ديسمبر ٢٠١٢'  |'الخميس، ٢٠ ديسمبر، ٢٠١٢' |
| Date.toLocaleString | 在英文下格式化日期 | 10/20/2022, 6:00:00 PM | 10/20/2022, 6:00:00 PM（PM前的空白字符变更） |
| Date.toLocaleTimeString | 在英文下格式化日期 | 6:00:00 PM | 6:00:00 PM（PM前的空白字符变更） |
| Intl.DateTimeFormat.format | 繁体中文下格式化2024年4月23日 | 2024年4月23日 | 2024 年 4 月 23 日 |
| Intl.DateTimeFormat.formatRange | 英式英语下格式化2020年12月20日至21日 | 20/12/2020 – 21/12/2020 | 20/12/2020 – 21/12/2020（日期间连接符变更） |
| Intl.DateTimeFormat.formatRangeToParts | 英语下格式化2020年12月20日至21日 | { type: "literal", value: " – " } | {"type":"literal","value":" – "}（value中空白字符变更）|
| Intl.ListFormat.format | 在中文下格式化列表 | Motorcycle、Bus和Car | Motorcycle、Bus、Car |
| Intl.RelativeTimeFormat.format | 英文下显示在1季度内 | in 1 qtr. | in 1q  |
| Intl.Locale.maximize | 区域ID为hy-arevmda | hyw | hyw-Armn-AM |
| Intl.Locale.minimize | 区域ID为und-150 | ru | en-150 |
| [ubrk_next](../../../application-dev/reference/native-lib/icu4c-symbol.md) | 对文本“service@baidu.com”进行分词解析 | @ 符号会与相邻字母粘连，“service@baidu.com”被识别为一个不可分割的整体。| @ 符号两侧会被识别为单词边界，被识别为“service”、“@”、“baidu.com”三个部分。 |

**适配指导**

接口默认效果变更，但开发者需审视此变更是否对自身相关业务展示效果产生影响，若有影响需根据自身业务代码进行对应适配。
