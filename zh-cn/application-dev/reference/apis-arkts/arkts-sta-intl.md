# Intl
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供国际化相关类型和格式化类，包括区域匹配、日期时间格式化、数字格式化、复数规则、相对时间格式化和分词能力。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## Intl

export namespace Intl

国际化能力命名空间。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

## 常用类型别名

### BCP47LanguageTag

type BCP47LanguageTag = string

BCP 47语言标签。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| string | BCP 47语言标签字符串，如`'zh-CN'`、`'en-US'`。 |

### DisplayNamesFallback

type DisplayNamesFallback = 'code' | 'none'

回退策略。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'code' | 当找不到对应代码的显示名称时回退显示代码本身。 |
| 'none' | 当找不到对应代码的显示名称时不进行回退。 |

### DisplayNamesLanguageDisplay

type DisplayNamesLanguageDisplay = 'dialect' | 'standard'

语言显示方式。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'dialect' | 按方言显示（如`'British English'`）。 |
| 'standard' | 按标准显示（如`'English (United Kingdom)'`）。 |

### DisplayNamesType

type DisplayNamesType = 'language' | 'region' | 'script' | 'calendar' | 'dateTimeField' | 'currency'

显示类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'language' | 语言名称。 |
| 'region' | 地区名称。 |
| 'script' | 书写系统名称。 |
| 'calendar' | 日历名称。 |
| 'dateTimeField' | 日期时间字段名称。 |
| 'currency' | 货币名称。 |

### ES2018NumberFormatPartType

type ES2018NumberFormatPartType = 'literal' | 'nan' | 'infinity' | 'percent' | 'integer' | 'group' | 'decimal' | 'fraction' | 'plusSign' | 'minusSign' | 'percentSign' | 'currency' | 'code' | 'symbol' | 'name'

ES2018数字格式化片段类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'literal' | 连接词或分隔符。 |
| 'nan' | NaN值。 |
| 'infinity' | 无穷大值。 |
| 'percent' | 百分比值（如50）。 |
| 'integer' | 整数部分。 |
| 'group' | 分组分隔符（如逗号）。 |
| 'decimal' | 小数点。 |
| 'fraction' | 小数部分。 |
| 'plusSign' | 正号。 |
| 'minusSign' | 负号。 |
| 'percentSign' | 百分号字符（%）。 |
| 'currency' | 货币符号。 |
| 'code' | 货币代码。 |
| 'symbol' | 货币符号。 |
| 'name' | 货币名称。 |

### ES2020NumberFormatPartType

type ES2020NumberFormatPartType = 'compact' | 'exponentInteger' | 'exponentMinusSign' | 'exponentSeparator' | 'unit' | 'unknown'

ES2020数字格式化片段类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'compact' | 紧凑表示（如K、M）。 |
| 'exponentInteger' | 指数的整数部分。 |
| 'exponentMinusSign' | 指数的负号。 |
| 'exponentSeparator' | 指数分隔符（如E）。 |
| 'unit' | 单位标识。 |
| 'unknown' | 未知类型。 |

### LDMLPluralRule

type LDMLPluralRule = 'zero' | 'one' | 'two' | 'few' | 'many' | 'other'

复数规则结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'zero' | 零。 |
| 'one' | 单数。 |
| 'two' | 双数。 |
| 'few' | 少数。 |
| 'many' | 多数。 |
| 'other' | 其他。 |

### ListFormatLocaleMatcher

type ListFormatLocaleMatcher = 'lookup' | 'best fit'

区域匹配策略。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'lookup' | 确定性匹配（按BCP 47算法逐步查找）。 |
| 'best fit' | 启发式匹配（选择最合适的区域）。 |

### ListFormatStyle

type ListFormatStyle = 'long' | 'short' | 'narrow'

格式样式。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'long' | 完整样式（如"A, B, and C"）。 |
| 'short' | 短样式（如"A, B & C"）。 |
| 'narrow' | 极简样式（如"A B C"）。 |

### ListFormatType

type ListFormatType = 'conjunction' | 'disjunction' | 'unit'

列表类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'conjunction' | "和"连接的列表（如"A, B, and C"）。 |
| 'disjunction' | "或"连接的列表（如"A, B, or C"）。 |
| 'unit' | 含单位的列表（如"5 pounds, 12 ounces"）。 |

### LocaleCollationCaseFirst

type LocaleCollationCaseFirst = 'upper' | 'lower' | 'false'

大小写排列顺序。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'upper' | 大写排前面。 |
| 'lower' | 小写排前面。 |
| 'false' | 使用区域默认的大小写排序规则。 |

### LocaleHourCycleKey

type LocaleHourCycleKey = 'h12' | 'h23' | 'h11' | 'h24'

小时周期。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'h11' | 0~11小时制。 |
| 'h12' | 1~12小时制。 |
| 'h23' | 0~23小时制。 |
| 'h24' | 1~24小时制。 |

### NumberFormatPartTypes

type NumberFormatPartTypes = ES2018NumberFormatPartType | ES2020NumberFormatPartType

数字格式化片段类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| [ES2018NumberFormatPartType](#es2018numberformatparttype) | ES2018数字格式化片段类型。 |
| [ES2020NumberFormatPartType](#es2020numberformatparttype) | ES2020数字格式化片段类型。 |

### PluralRuleType

type PluralRuleType = 'cardinal' | 'ordinal'

复数规则类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'cardinal' | 基数（表示数量）。 |
| 'ordinal' | 序数（表示顺序）。 |

### RelativeTimeFormatLocaleMatcher

type RelativeTimeFormatLocaleMatcher = 'lookup' | 'best fit'

区域匹配策略。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'lookup' | 确定性匹配（按BCP 47算法逐步查找）。 |
| 'best fit' | 启发式匹配（选择最合适的区域）。 |

### RelativeTimeFormatNumeric

type RelativeTimeFormatNumeric = 'always' | 'auto'

数值显示方式。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'always' | 始终使用数字表示（如"1 day ago"）。 |
| 'auto' | 自动选择（如"yesterday"）。 |

### RelativeTimeFormatStyle

type RelativeTimeFormatStyle = 'long' | 'short' | 'narrow'

格式样式。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'long' | 完整样式（如"in 1 day"）。 |
| 'short' | 短样式（如"in 1 day"缩写）。 |
| 'narrow' | 极简样式。 |

### RelativeTimeFormatUnit

type RelativeTimeFormatUnit = 'year' | 'years' | 'quarter' | 'quarters' | 'month' | 'months' | 'week' | 'weeks' | 'day' | 'days' | 'hour' | 'hours' | 'minute' | 'minutes' | 'second' | 'seconds'

时间单位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'year' | 年。 |
| 'years' | 年（复数）。 |
| 'quarter' | 季度。 |
| 'quarters' | 季度（复数）。 |
| 'month' | 月。 |
| 'months' | 月（复数）。 |
| 'week' | 周。 |
| 'weeks' | 周（复数）。 |
| 'day' | 日。 |
| 'days' | 日（复数）。 |
| 'hour' | 时。 |
| 'hours' | 时（复数）。 |
| 'minute' | 分。 |
| 'minutes' | 分（复数）。 |
| 'second' | 秒。 |
| 'seconds' | 秒（复数）。 |

### RelativeTimeFormatUnitSingular

type RelativeTimeFormatUnitSingular = 'year' | 'quarter' | 'month' | 'week' | 'day' | 'hour' | 'minute' | 'second'

单数形式时间单位。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'year' | 年。 |
| 'quarter' | 季度。 |
| 'month' | 月。 |
| 'week' | 周。 |
| 'day' | 日。 |
| 'hour' | 时。 |
| 'minute' | 分。 |
| 'second' | 秒。 |

### UnicodeBCP47LocaleIdentifier

type UnicodeBCP47LocaleIdentifier = string

Unicode BCP 47区域标识符。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| string | Unicode BCP 47区域标识符字符串，如`'zh-CN'`、`'en-US'`。 |

### DateTimeFormatPartTypes

type DateTimeFormatPartTypes = 'day' | 'dayPeriod' | 'era' | 'fractionalSecond' | 'hour' | 'literal' | 'minute' | 'month' | 'second' | 'timeZoneName' | 'unknown' | 'weekday' | 'year'

日期时间格式化片段类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'day' | 日。 |
| 'dayPeriod' | 日间时段（如AM/PM）。 |
| 'era' | 纪元。 |
| 'fractionalSecond' | 小数秒。 |
| 'hour' | 小时。 |
| 'literal' | 连接词或分隔符。 |
| 'minute' | 分钟。 |
| 'month' | 月份。 |
| 'second' | 秒。 |
| 'timeZoneName' | 时区名称。 |
| 'unknown' | 未知类型。 |
| 'weekday' | 星期。 |
| 'year' | 年。 |

### DateTimeRangeFormatPartSource

type DateTimeRangeFormatPartSource = 'startRange' | 'endRange' | 'shared'

日期时间范围片段来源。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| 'startRange' | 片段来自起始时间。 |
| 'endRange' | 片段来自结束时间。 |
| 'shared' | 片段为起始和结束时间共用。 |

### LocalesArgument

type LocalesArgument = UnicodeBCP47LocaleIdentifier | Locale | readonly (UnicodeBCP47LocaleIdentifier | Locale)[]

区域参数类型，支持单个区域标识符字符串、Locale对象或它们的只读数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| [UnicodeBCP47LocaleIdentifier](#unicodebcp47localeidentifier) | 单个区域标识符字符串。 |
| [Locale](#locale) | Locale对象。 |
| readonly ([UnicodeBCP47LocaleIdentifier](#unicodebcp47localeidentifier) \| [Locale](#locale))[] | 区域标识符字符串或Locale对象的只读数组。 |

## intlLookUpLocale

intlLookUpLocale(locale: Intl.BCP47LanguageTag | Intl.BCP47LanguageTag[]): string

使用lookup策略从候选区域中选择最匹配的区域标签。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locale | [Intl.BCP47LanguageTag](#bcp47languagetag) \| [Intl.BCP47LanguageTag](#bcp47languagetag)[] | 是 | 单个BCP 47语言标签或语言标签数组。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 匹配到的区域标签。 |

**示例：**

```ts
let locale = Intl.intlLookUpLocale("en-US");
console.info(locale); // "en-US"

locale = Intl.intlLookUpLocale(["fr-CA", "en-US"]);
console.info(locale); // "fr-CA"
```

## intlBestFitLocale

intlBestFitLocale(locale: Intl.BCP47LanguageTag | Intl.BCP47LanguageTag[]): string

使用best fit策略从候选区域中选择最匹配的区域标签。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locale | [Intl.BCP47LanguageTag](#bcp47languagetag) \| [Intl.BCP47LanguageTag](#bcp47languagetag)[] | 是 | 单个BCP 47语言标签或语言标签数组。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 匹配到的区域标签。 |

**示例：**

```ts
let locale = Intl.intlBestFitLocale("zh-Hans-CN");
console.info(locale); // "zh-Hans-CN"

locale = Intl.intlBestFitLocale(["ja-JP", "en-US"]);
console.info(locale); // "ja-JP"
```

## intlLookUpLocales

intlLookUpLocales(locale: Intl.BCP47LanguageTag | Intl.BCP47LanguageTag[]): string[]

使用lookup策略返回匹配到的区域标签列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locale | [Intl.BCP47LanguageTag](#bcp47languagetag) \| [Intl.BCP47LanguageTag](#bcp47languagetag)[] | 是 | 单个BCP 47语言标签或语言标签数组。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 匹配到的区域标签列表。 |

**示例：**

```ts
let locales = Intl.intlLookUpLocales(["en-US", "zh-CN"]);
console.info(locales.length); // 2
console.info(locales[0]); // "en-US"

locales = Intl.intlLookUpLocales("ja-JP");
console.info(locales.length); // 1
```

## intlBestFitLocales

intlBestFitLocales(locale: Intl.BCP47LanguageTag | Intl.BCP47LanguageTag[]): string[]

使用best fit策略返回匹配到的区域标签列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locale | [Intl.BCP47LanguageTag](#bcp47languagetag) \| [Intl.BCP47LanguageTag](#bcp47languagetag)[] | 是 | 单个BCP 47语言标签或语言标签数组。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 匹配到的区域标签列表。 |

**示例：**

```ts
let locales = Intl.intlBestFitLocales(["en-US", "zh-CN"]);
console.info(locales.length); // 2

locales = Intl.intlBestFitLocales("ko-KR");
console.info(locales[0]); // "ko-KR"
```

## intlLocalesToLanguageTags

intlLocalesToLanguageTags(locales: string | Intl.Locale | ReadonlyArray\<string | Intl.Locale> | undefined): string[]

将区域参数规范化为语言标签数组。传入`undefined`时返回空数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| [Intl.Locale](#locale) \| ReadonlyArray<string \| [Intl.Locale](#locale)> \| undefined | 是 | 待规范化的区域参数。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 规范化后的语言标签数组。 |

**示例：**

```ts
let tags = Intl.intlLocalesToLanguageTags("en-US");
console.info(tags[0]); // "en-US"

tags = Intl.intlLocalesToLanguageTags(new Intl.Locale("zh-CN"));
console.info(tags[0]); // "zh-CN"

tags = Intl.intlLocalesToLanguageTags(undefined);
console.info(tags.length); // 0
```

## ResolvedCollatorOptions

export interface ResolvedCollatorOptions

Collator解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| caseFirst | string | 否 | 否 | 大小写排列顺序，取值包括：<br>`'upper'`：大写排前面。<br>`'lower'`：小写排前面。<br>`'false'`：使用区域默认的大小写排序规则。 |
| collation | string | 否 | 否 | 排序规则，取值包括：<br>`'big5han'`：Big5拼音排序（拉丁字母使用的拼音排序）。<br>`'compat'`：兼容性排序，仅用于阿拉伯语。<br>`'dict'`：词典风格排序，仅用于僧伽罗语。<br>`'direct'`：二进制码点排序。<br>`'ducet'`：按Unicode排序元素表排序。<br>`'eor'`：按欧洲排序规则排序。<br>`'gb2312'`：GB2312拼音排序，仅用于中文排序。<br>`'phonebk'`：电话本风格排序。<br>`'phonetic'`：发音排序。<br>`'pinyin'`：拼音排序。<br>`'reformed'`：瑞典语排序。<br>`'searchjl'`：韩语初始辅音搜索的特殊排序。<br>`'stroke'`：笔画排序，仅用于中文排序。<br>`'trad'`：传统风格排序，如西班牙语。<br>`'unihan'`：统一汉字排序，用于日语、韩语、中文等汉字排序。<br>`'zhuyin'`：注音排序，仅用于中文排序。 |
| ignorePunctuation | boolean | 否 | 否 | 是否忽略标点，`true`表示忽略标点符号，`false`表示考虑标点符号。 |
| locale | string | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| numeric | boolean | 否 | 否 | 是否使用数字排序，`true`表示使用数字排序（如'1' < '2' < '10'），`false`表示不使用数字排序（如'1' < '10' < '2'）。 |
| sensitivity | string | 否 | 否 | 比较敏感度，取值包括：<br>`'base'`：不同的字母比较不相等，如'a' ≠ 'b', 'a' = 'á', 'a' = 'A'。<br>`'accent'`：不同的字母或不同读音的相同字母比较不相等，如'a' ≠ 'b', 'a' ≠ 'á', 'a' = 'A'。<br>`'case'`：不同的字母或相同字母大小写比较不相等，如'a' ≠ 'b', 'a' = 'á', 'a' ≠ 'A'。<br>`'variant'`：不同的字母或读音及其它有区别的标志或大小写都是不相等的，如'a' ≠ 'b', 'a' ≠ 'á', 'a' ≠ 'A'。 |
| usage | string | 否 | 否 | 比较用途，取值包括：<br>`'sort'`：用作排序。<br>`'search'`：用作查找匹配的字符串。 |

## CollatorOptions

export interface CollatorOptions

Collator构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| caseFirst | string \| undefined | 否 | 是 | 大小写排列顺序，取值包括：<br>`'upper'`：大写排前面。<br>`'lower'`：小写排前面。<br>`'false'`：使用区域默认的大小写排序规则；默认为`'false'`。 |
| collation | string \| undefined | 否 | 是 | 排序规则，取值包括：<br>`'big5han'`：Big5拼音排序（拉丁字母使用的拼音排序）。<br>`'compat'`：兼容性排序，仅用于阿拉伯语。<br>`'dict'`：词典风格排序，仅用于僧伽罗语。<br>`'direct'`：二进制码点排序。<br>`'ducet'`：按Unicode排序元素表排序。<br>`'eor'`：按欧洲排序规则排序。<br>`'gb2312'`：GB2312拼音排序，仅用于中文排序。<br>`'phonebk'`：电话本风格排序。<br>`'phonetic'`：发音排序。<br>`'pinyin'`：拼音排序。<br>`'reformed'`：瑞典语排序。<br>`'searchjl'`：韩语初始辅音搜索的特殊排序。<br>`'stroke'`：笔画排序，仅用于中文排序。<br>`'trad'`：传统风格排序，如西班牙语。<br>`'unihan'`：统一汉字排序，用于日语、韩语、中文等汉字排序。<br>`'zhuyin'`：注音排序，仅用于中文排序；默认为`'default'`。 |
| ignorePunctuation | boolean \| undefined | 否 | 是 | 是否忽略标点，`true`表示忽略标点符号，`false`表示考虑标点符号；默认为`false`。 |
| localeMatcher | string \| undefined | 否 | 是 | 区域匹配策略，取值包括：<br>`'lookup'`：确定性匹配（按BCP 47算法逐步查找）。<br>`'best fit'`：启发式匹配（选择最合适的区域）；默认为`'best fit'`。 |
| numeric | boolean \| undefined | 否 | 是 | 是否使用数字排序，`true`表示使用数字排序（如'1' < '2' < '10'），`false`表示不使用数字排序（如'1' < '10' < '2'）；默认为`false`。 |
| sensitivity | string \| undefined | 否 | 是 | 比较敏感度，取值包括：<br>`'base'`：不同的字母比较不相等，如'a' ≠ 'b', 'a' = 'á', 'a' = 'A'。<br>`'accent'`：不同的字母或不同读音的相同字母比较不相等，如'a' ≠ 'b', 'a' ≠ 'á', 'a' = 'A'。<br>`'case'`：不同的字母或相同字母大小写比较不相等，如'a' ≠ 'b', 'a' = 'á', 'a' ≠ 'A'。<br>`'variant'`：不同的字母或读音及其它有区别的标志或大小写都是不相等的，如'a' ≠ 'b', 'a' ≠ 'á', 'a' ≠ 'A'；默认为`'variant'`。 |
| usage | string \| undefined | 否 | 是 | 比较用途，取值包括：<br>`'sort'`：用作排序。<br>`'search'`：用作查找匹配的字符串；默认为`'sort'`。 |

## Collator

export class Collator

字符串比较器，用于区域敏感的字符串排序和搜索。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: string | string[], options?: CollatorOptions)

创建Collator对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [CollatorOptions](#collatoroptions) | 否 | 比较选项；默认各属性取默认值。 |

**示例：**

```ts
let collator = new Intl.Collator("en-US");
console.info(collator.compare("a", "b")); // -1
```

### compare

compare(x: string, y: string): int

比较两个字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | string | 是 | 待比较的第一个字符串。 |
| y | string | 是 | 待比较的第二个字符串。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| int | `x`大于`y`时返回`1`；`x`小于`y`时返回`-1`；相等时返回`0`。 |

**示例：**

```ts
// 不使用options
const collator = new Intl.Collator("en-US");
console.info(collator.compare("a", "b")); // -1
console.info(collator.compare("b", "a")); // 1
console.info(collator.compare("a", "a")); // 0

// numeric为true时按数值排序
let numericCollator = new Intl.Collator("en-US", { numeric: true });
console.info(numericCollator.compare("1", "10")); // -1
console.info(numericCollator.compare("2", "10")); // -1
console.info(numericCollator.compare("10", "11")); // -1

// sensitivity为'base'时忽略大小写和音调差异
let baseCollator = new Intl.Collator("de-DE", { sensitivity: 'base' });
console.info(baseCollator.compare("a", "A")); // 0
console.info(baseCollator.compare("a", "ä")); // 0

// sensitivity为'case'时区分大小写但忽略音调
let caseCollator = new Intl.Collator("de-DE", { sensitivity: 'case' });
console.info(caseCollator.compare("a", "A")); // -1
console.info(caseCollator.compare("a", "ä")); // 0

// caseFirst为'upper'时大写排前面
let upperCollator = new Intl.Collator("en-US", { caseFirst: 'upper' });
console.info(upperCollator.compare("A", "a")); // -1

// caseFirst为'lower'时小写排前面
let lowerCollator = new Intl.Collator("en-US", { caseFirst: 'lower' });
console.info(lowerCollator.compare("a", "A")); // -1

// ignorePunctuation为true时忽略标点
let noPunctCollator = new Intl.Collator("en-US", { ignorePunctuation: true });
console.info(noPunctCollator.compare("hello", "hello!")); // 0
```

### resolvedOptions

resolvedOptions(): ResolvedCollatorOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedCollatorOptions](#resolvedcollatoroptions) | 解析后的选项。 |

**示例：**

```ts
const collator = new Intl.Collator("en-US", { sensitivity: "base" });
const options = collator.resolvedOptions();
console.info(options.locale); // "en-US"
console.info(options.sensitivity); // "base"
console.info(options.usage); // "sort"
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | string[], options?: CollatorOptions): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 是 | 待检查的区域标签或区域标签数组。 |
| options | [CollatorOptions](#collatoroptions) | 否 | 区域匹配选项；默认options.localeMatcher为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.Collator.supportedLocalesOf(["en-US", "zh-CN"]);
console.info(supported.length); // 2

supported = Intl.Collator.supportedLocalesOf(["en-US"], { localeMatcher: "lookup" });
console.info(supported[0]); // "en-US"
```

## ResolvedDateTimeFormatOptions

export interface ResolvedDateTimeFormatOptions

DateTimeFormat解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| calendar | string | 否 | 否 | 日历类型，如`'gregory'`、`'chinese'`、`'islamic'`、`'hebrew'`等。 |
| dateStyle | 'full' \| 'long' \| 'medium' \| 'short' | 否 | 是 | 日期样式，`'full'`为完整样式，`'long'`为长样式，`'medium'`为中等样式，`'short'`为短样式。未设置时该属性不存在。 |
| day | 'numeric' \| '2-digit' | 否 | 是 | 日的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）。未指定任何日期时间属性时默认为`'numeric'`。 |
| dayPeriod | 'narrow' \| 'short' \| 'long' | 否 | 是 | 日间时段的格式，`'narrow'`为缩写，`'short'`为短格式，`'long'`为长格式，如AM/PM或上午/下午。未设置时该属性不存在。 |
| era | 'long' \| 'short' \| 'narrow' | 否 | 是 | 纪元的格式，`'long'`为完整名称（如Anno Domini），`'short'`为缩写（如AD），`'narrow'`为极简缩写（如A）。未设置时该属性不存在。 |
| formatMatcher | 'basic' \| 'best fit' | 否 | 是 | 格式匹配策略，`'basic'`为基本匹配，`'best fit'`为最佳匹配。未设置时该属性不存在。 |
| fractionalSecondDigits | int | 否 | 是 | 小数秒位数（1~3）。未设置时该属性不存在。 |
| hour12 | boolean | 否 | 是 | 是否使用12小时制；默认根据hourCycle推断，hourCycle为`'h11'`或`'h12'`时为`true`，为`'h23'`或`'h24'`时为`false`。 |
| hour | 'numeric' \| '2-digit' | 否 | 是 | 小时的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）。未设置时该属性不存在。 |
| hourCycle | 'h11' \| 'h12' \| 'h23' \| 'h24' | 否 | 是 | 小时周期，`'h11'`表示0~11小时制，`'h12'`表示1~12小时制，`'h23'`表示0~23小时制，`'h24'`表示1~24小时制；默认根据区域推断。 |
| locale | string | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| minute | 'numeric' \| '2-digit' | 否 | 是 | 分钟的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）。未设置时该属性不存在。 |
| month | 'numeric' \| '2-digit' \| 'long' \| 'short' \| 'narrow' | 否 | 是 | 月份的格式，`'numeric'`为数字不补零（如1），`'2-digit'`为数字补零（如01），`'long'`为完整名称（如January），`'short'`为缩写（如Jan），`'narrow'`为极简缩写（如J）。未指定任何日期时间属性时默认为`'numeric'`。 |
| numberingSystem | string | 否 | 否 | 数字系统，如`'latn'`（拉丁数字）、`'arab'`（阿拉伯数字）、`'hans'`（简体中文数字）等。 |
| second | 'numeric' \| '2-digit' | 否 | 是 | 秒的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）。未设置时该属性不存在。 |
| timeStyle | 'full' \| 'long' \| 'medium' \| 'short' | 否 | 是 | 时间样式，`'full'`为完整样式，`'long'`为长样式，`'medium'`为中等样式，`'short'`为短样式。未设置时该属性不存在。 |
| timeZone | string | 否 | 否 | 时区，IANA时区名称，如`'Asia/Shanghai'`、`'America/New_York'`。 |
| timeZoneName | 'short' \| 'long' \| 'shortOffset' \| 'longOffset' \| 'shortGeneric' \| 'longGeneric' | 否 | 是 | 时区名称的格式，`'short'`为短名称（如PST），`'long'`为长名称（如Pacific Standard Time），`'shortOffset'`为短偏移格式（如GMT-8），`'longOffset'`为长偏移格式（如GMT-08:00），`'shortGeneric'`为短通用名称（如PT），`'longGeneric'`为长通用名称（如Pacific Time）。未设置时该属性不存在。 |
| weekday | 'long' \| 'short' \| 'narrow' | 否 | 是 | 星期的格式，`'long'`为完整名称（如Monday），`'short'`为缩写（如Mon），`'narrow'`为极简缩写（如M）。未设置时该属性不存在。 |
| year | 'numeric' \| '2-digit' | 否 | 是 | 年的格式，`'numeric'`为完整年份（如2024），`'2-digit'`为两位数年份（如24）。未指定任何日期时间属性时默认为`'numeric'`。 |

## DateTimeFormatPart

export interface DateTimeFormatPart

日期时间格式化片段。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | [DateTimeFormatPartTypes](#datetimeformatparttypes) | 否 | 否 | 片段类型，如`'year'`、`'month'`、`'day'`、`'hour'`等，表示该片段属于日期时间的哪个部分。 |
| value | string | 否 | 否 | 片段值，对应type的格式化结果字符串，如type为`'month'`时value可能为`"January"`或`"01"`。 |

## DateTimeRangeFormatPart
export interface DateTimeRangeFormatPart extends DateTimeFormatPart

日期时间范围格式化片段。继承自[DateTimeFormatPart](#datetimeformatpart)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | [DateTimeFormatPartTypes](#datetimeformatparttypes) | 否 | 否 | 片段类型，如`'year'`、`'month'`、`'day'`、`'hour'`等，表示该片段属于日期时间的哪个部分。 |
| value | string | 否 | 否 | 片段值，对应type的格式化结果字符串。 |
| source | [DateTimeRangeFormatPartSource](#datetimerangeformatpartsource) | 否 | 否 | 片段来源，`'startRange'`表示片段来自起始时间，`'endRange'`表示片段来自结束时间，`'shared'`表示片段为起始和结束时间共用。 |

## DateTimeFormatOptions

export interface DateTimeFormatOptions

DateTimeFormat构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| calendar | string | 否 | 是 | 日历类型，如`'gregory'`、`'chinese'`、`'islamic'`、`'hebrew'`等；默认为`undefined`。 |
| localeMatcher | 'lookup' \| 'best fit' | 否 | 是 | 区域匹配策略，`'lookup'`为确定性匹配（按BCP 47算法逐步查找），`'best fit'`为启发式匹配（选择最合适的区域）；默认为`'best fit'`。 |
| dateStyle | 'full' \| 'long' \| 'medium' \| 'short' | 否 | 是 | 日期样式，`'full'`为完整样式，`'long'`为长样式，`'medium'`为中等样式，`'short'`为短样式；默认为`undefined`。 |
| day | 'numeric' \| '2-digit' | 否 | 是 | 日的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）；未指定任何日期时间属性时默认为`'numeric'`。 |
| dayPeriod | 'narrow' \| 'short' \| 'long' | 否 | 是 | 日间时段的格式，`'narrow'`为缩写，`'short'`为短格式，`'long'`为长格式，如AM/PM或上午/下午；默认为`undefined`。 |
| era | 'long' \| 'short' \| 'narrow' | 否 | 是 | 纪元的格式，`'long'`为完整名称（如Anno Domini），`'short'`为缩写（如AD），`'narrow'`为极简缩写（如A）；默认为`undefined`。 |
| formatMatcher | 'basic' \| 'best fit' | 否 | 是 | 格式匹配策略，`'basic'`为基本匹配，`'best fit'`为最佳匹配；默认为`undefined`。 |
| fractionalSecondDigits | int | 否 | 是 | 小数秒位数，取值范围1~3；默认为`undefined`。 |
| hour12 | boolean | 否 | 是 | 是否使用12小时制，`true`表示使用12小时制，`false`表示使用24小时制；默认为`undefined`（由hourCycle和区域决定）。 |
| hour | 'numeric' \| '2-digit' | 否 | 是 | 小时的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）；默认为`undefined`。 |
| hourCycle | 'h11' \| 'h12' \| 'h23' \| 'h24' | 否 | 是 | 小时周期，`'h11'`表示0~11小时制，`'h12'`表示1~12小时制，`'h23'`表示0~23小时制，`'h24'`表示1~24小时制；默认为`undefined`（由区域决定）。 |
| minute | 'numeric' \| '2-digit' | 否 | 是 | 分钟的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）；默认为`undefined`。 |
| month | 'numeric' \| '2-digit' \| 'long' \| 'short' \| 'narrow' | 否 | 是 | 月份的格式，`'numeric'`为数字不补零（如1），`'2-digit'`为数字补零（如01），`'long'`为完整名称（如January），`'short'`为缩写（如Jan），`'narrow'`为极简缩写（如J）；未指定任何日期时间属性时默认为`'numeric'`。 |
| numberingSystem | string | 否 | 是 | 数字系统，如`'latn'`（拉丁数字）、`'arab'`（阿拉伯数字）、`'hans'`（简体中文数字）等；默认为`undefined`。 |
| second | 'numeric' \| '2-digit' | 否 | 是 | 秒的格式，`'numeric'`为个位数不补零（如1），`'2-digit'`为个位数补零（如01）；默认为`undefined`。 |
| timeStyle | 'full' \| 'long' \| 'medium' \| 'short' | 否 | 是 | 时间样式，`'full'`为完整样式，`'long'`为长样式，`'medium'`为中等样式，`'short'`为短样式；默认为`undefined`。 |
| timeZone | string | 否 | 是 | 时区，IANA时区名称，如`'Asia/Shanghai'`、`'America/New_York'`；默认为`undefined`。 |
| timeZoneName | 'short' \| 'long' \| 'shortOffset' \| 'longOffset' \| 'shortGeneric' \| 'longGeneric' | 否 | 是 | 时区名称的格式，`'short'`为短名称（如PST），`'long'`为长名称（如Pacific Standard Time），`'shortOffset'`为短偏移格式（如GMT-8），`'longOffset'`为长偏移格式（如GMT-08:00），`'shortGeneric'`为短通用名称（如PT），`'longGeneric'`为长通用名称（如Pacific Time）；默认为`undefined`。 |
| weekday | 'long' \| 'short' \| 'narrow' | 否 | 是 | 星期的格式，`'long'`为完整名称（如Monday），`'short'`为缩写（如Mon），`'narrow'`为极简缩写（如M）；默认为`undefined`。 |
| year | 'numeric' \| '2-digit' | 否 | 是 | 年的格式，`'numeric'`为完整年份（如2024），`'2-digit'`为两位数年份（如24）；未指定任何日期时间属性时默认为`'numeric'`。 |

## DateTimeFormat

export class DateTimeFormat

日期时间格式化器，用于区域敏感的日期时间格式化。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: string | string[], options?: DateTimeFormatOptions)

创建DateTimeFormat对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [DateTimeFormatOptions](#datetimeformatoptions) | 否 | 格式化选项；默认各属性取默认值。 |

**示例：**

```ts
let dtf = new Intl.DateTimeFormat("en-US");
console.info(dtf.format(new Date(2024, 0, 15))); // "1/15/2024"

dtf = new Intl.DateTimeFormat("zh-CN");
console.info(dtf.format(new Date(2024, 0, 15))); // "2024/1/15"

dtf = new Intl.DateTimeFormat("en-US", { weekday: "long", year: "numeric", month: "long", day: "numeric" });
console.info(dtf.format(new Date(2024, 0, 15))); // "Monday, January 15, 2024"
```

### format

format(date?: Date | double): string

格式化日期时间。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| date | Date \| double | 否 | 待格式化的日期；省略时使用当前时间。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 格式化后的日期时间字符串。 |

**示例：**

```ts
let dtf = new Intl.DateTimeFormat("en-US");
console.info(dtf.format(new Date(2024, 0, 15))); // "1/15/2024"

dtf = new Intl.DateTimeFormat("en-US", { dateStyle: "full" });
console.info(dtf.format(new Date(2024, 5, 1))); // "Saturday, June 1, 2024"

console.info(dtf.format()); // 格式化当前时间
```

### formatToParts

formatToParts(date?: Date | double): DateTimeFormatPart[]

将日期时间格式化为片段数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| date | Date \| double | 否 | 待格式化的日期；省略时使用当前时间。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [DateTimeFormatPart](#datetimeformatpart)[] | 格式化后的片段数组。 |

**示例：**

```ts
const dtf = new Intl.DateTimeFormat("en-US", { year: "numeric", month: "long", day: "numeric" });
const parts = dtf.formatToParts(new Date(2024, 0, 15));
for (const part of parts) {
    console.info(part.type + ": " + part.value);
}
// month: January, literal: , day: 15, literal: ,year: 2024
```

### formatRange

formatRange(startDate: Date | double, endDate: Date | double): string

格式化日期时间范围。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| startDate | Date \| double | 是 | 范围起始日期。 |
| endDate | Date \| double | 是 | 范围结束日期。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 格式化后的日期时间范围字符串。 |

**示例：**

```ts
const dtf = new Intl.DateTimeFormat("en-US", { year: "numeric", month: "short", day: "numeric" });
const start = new Date(2024, 0, 1);
const end = new Date(2024, 0, 15);
console.info(dtf.formatRange(start, end)); // "Jan 1 – 15, 2024"
```

### formatRangeToParts

formatRangeToParts(startDate: Date | double, endDate: Date | double): DateTimeRangeFormatPart[]

将日期时间范围格式化为片段数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| startDate | Date \| double | 是 | 范围起始日期。 |
| endDate | Date \| double | 是 | 范围结束日期。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [DateTimeRangeFormatPart](#datetimerangeformatpart)[] | 格式化后的片段数组。 |

**示例：**

```ts
const dtf = new Intl.DateTimeFormat("en-US");
const start = new Date(2024, 1, 10);
const end = new Date(2024, 1, 15);
const parts = dtf.formatRangeToParts(start, end);
for (const part of parts) {
    console.info(part.source + ": " + part.type + "=" + part.value);
}
// startRange: month=2
// startRange: literal=/
// startRange: day=10
// startRange: literal=/
// startRange: year=2024
// shared: literal= – 
// endRange: month=2
// endRange: literal=/
// endRange: day=15
// endRange: literal=/
// endRange: year=2024
```

### resolvedOptions

resolvedOptions(): ResolvedDateTimeFormatOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedDateTimeFormatOptions](#resolveddatetimeformatoptions) | 解析后的选项。 |

**示例：**

```ts
const dtf = new Intl.DateTimeFormat("en-US", { hour: "numeric", minute: "numeric" });
const options = dtf.resolvedOptions();
console.info(options.locale); // "en-US"
console.info(options.numberingSystem); // "latn"
console.info(options.calendar); // "gregory"
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | Locale | ReadonlyArray<string | Locale>, options?: DateTimeFormatOptions): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| [Locale](#locale) \| ReadonlyArray<string \| [Locale](#locale)> | 是 | 待检查的区域。 |
| options | [DateTimeFormatOptions](#datetimeformatoptions) | 否 | 区域匹配选项；默认options.localeMatcher为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.DateTimeFormat.supportedLocalesOf(["en-US", "zh-CN"]);
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,zh-CN"

supported = Intl.DateTimeFormat.supportedLocalesOf(["xxx"], { localeMatcher: "lookup" });
console.info(supported.length); // 0
```

## DisplayNamesOptions

export interface DisplayNamesOptions

DisplayNames构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| fallback | [DisplayNamesFallback](#displaynamesfallback) | 否 | 是 | 回退策略；默认为`'code'`。 |
| languageDisplay | [DisplayNamesLanguageDisplay](#displaynameslanguagedisplay) | 否 | 是 | 语言显示方式，仅在type为`'language'`时生效；默认为`'dialect'`。 |
| localeMatcher | [RelativeTimeFormatLocaleMatcher](#relativetimeformatlocalematcher) | 否 | 是 | 区域匹配策略；默认为`'best fit'`。 |
| style | [RelativeTimeFormatStyle](#relativetimeformatstyle) | 否 | 是 | 显示样式；默认为`'long'`。 |
| type | [DisplayNamesType](#displaynamestype) | 否 | 否 | 显示类型（必填）。 |

## DisplayNamesLocaleMatcherOptions

export interface DisplayNamesLocaleMatcherOptions

DisplayNames区域匹配选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| localeMatcher | [RelativeTimeFormatLocaleMatcher](#relativetimeformatlocalematcher) | 否 | 是 | 区域匹配策略；默认为`'best fit'`。 |

## ResolvedDisplayNamesOptions

export interface ResolvedDisplayNamesOptions

DisplayNames解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| fallback | [DisplayNamesFallback](#displaynamesfallback) | 否 | 否 | 回退策略。 |
| languageDisplay | [DisplayNamesLanguageDisplay](#displaynameslanguagedisplay) | 否 | 是 | 语言显示方式，仅在type为`'language'`时存在；默认为`'dialect'`。 |
| locale | [UnicodeBCP47LocaleIdentifier](#unicodebcp47localeidentifier) | 否 | 否 | 区域标识符，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| style | [RelativeTimeFormatStyle](#relativetimeformatstyle) | 否 | 否 | 显示样式。 |
| type | [DisplayNamesType](#displaynamestype) | 否 | 否 | 显示类型。 |

## DisplayNames

export class DisplayNames

区域敏感的显示名称格式化器，用于获取语言、区域、脚本等的本地化名称。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: BCP47LanguageTag | BCP47LanguageTag[], options?: DisplayNamesOptions)

创建DisplayNames对象。`options`为`undefined`时抛出`TypeError`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | BCP47LanguageTag \| BCP47LanguageTag[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [DisplayNamesOptions](#displaynamesoptions) | 否 | 显示名称选项（type为必填）；其余属性默认取默认值。 |

**错误信息：**

| 错误信息 | 说明 |
| :--- | :--- |
| TypeError | 未传入options参数或options中未指定type属性时抛出。<br>可能原因：未传入options参数，或options中未指定type属性。<br>处理步骤：确保调用时传入options对象，且options中包含有效的type属性。 |

**示例：**

```ts
let dn = new Intl.DisplayNames("en-US", { type: "language" });
console.info(dn.of("zh")); // "Chinese"
console.info(dn.of("ja")); // "Japanese"

dn = new Intl.DisplayNames("zh-CN", { type: "region" });
console.info(dn.of("US")); // "美国"

dn = new Intl.DisplayNames("en-US", { type: "currency" });
console.info(dn.of("CNY")); // "Chinese Yuan"

try {
  new Intl.DisplayNames("en-US"); // options为undefined，抛出TypeError
} catch (e) {
  console.info((e as TypeError).message); // "Options parameter is required"
}
```

### of

of(code: string): string | undefined

返回指定代码的本地化显示名称。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| code | string | 是 | 待查询的代码。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string \| undefined | 本地化显示名称；无匹配且回退策略为`'none'`时返回`undefined`。 |

**示例：**

```ts
const dn = new Intl.DisplayNames("en-US", { type: "language" });
console.info(dn.of("zh")); // "Chinese"
console.info(dn.of("en")); // "English"

const dnRegion = new Intl.DisplayNames("en-US", { type: "region" });
console.info(dnRegion.of("CN")); // "China"
```

### resolvedOptions

resolvedOptions(): ResolvedDisplayNamesOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedDisplayNamesOptions](#resolveddisplaynamesoptions) | 解析后的选项。 |

**示例：**

```ts
const dn = new Intl.DisplayNames("en-US", { type: "language" });
const options = dn.resolvedOptions();
console.info(options.locale); // "en-US"
console.info(options.type); // "language"
console.info(options.style); // "long"
console.info(options.fallback); // "code"
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | Locale | FixedArray<string | Locale>): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | BCP47LanguageTag \| [Locale](#locale) \| FixedArray<string \| [Locale](#locale)> | 是 | 待检查的区域。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.DisplayNames.supportedLocalesOf("en-US");
console.info(supported.length); // 1
console.info(supported[0]); // "en-US"

let locales: FixedArray<string> = ["en-US", "zh-CN"];
supported = Intl.DisplayNames.supportedLocalesOf(locales);
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,zh-CN"
```

## ListFormatOptions

export interface ListFormatOptions

ListFormat构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| localeMatcher | [ListFormatLocaleMatcher](#listformatlocalematcher) \| undefined | 否 | 是 | 区域匹配策略；默认为`'best fit'`。 |
| style | [ListFormatStyle](#listformatstyle) \| undefined | 否 | 是 | 格式样式；默认为`'long'`。 |
| type | [ListFormatType](#listformattype) \| undefined | 否 | 是 | 列表类型；默认为`'conjunction'`。 |

## FormatToPartsResult

export interface FormatToPartsResult

ListFormat格式化片段结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | 'element' \| 'literal' | 否 | 否 | 片段类型，`'element'`为列表元素值，`'literal'`为连接词或分隔符（如", "、"and "）。 |
| value | string | 否 | 否 | 片段值，当type为`'element'`时为列表中的元素内容，当type为`'literal'`时为连接词或分隔符字符串。 |

## ListFormat

export class ListFormat

列表格式化器，用于区域敏感的列表拼接。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: string | string[], options?: ListFormatOptions)

创建ListFormat对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [ListFormatOptions](#listformatoptions) | 否 | 列表格式化选项；默认各属性取默认值。 |

**示例：**

```ts
let lf = new Intl.ListFormat("en-US");
console.info(lf.format(["Apple", "Banana", "Orange"])); // "Apple, Banana, and Orange"

lf = new Intl.ListFormat("en-US", { style: "short", type: "conjunction" });
console.info(lf.format(["Apple", "Banana"])); // "Apple & Banana"

lf = new Intl.ListFormat("zh-CN", { type: "disjunction" });
console.info(lf.format(["苹果", "香蕉"])); // "苹果或香蕉"
```

### format

format(list: Iterable\<string>): string

格式化列表为字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| list | Iterable\<string> | 是 | 待格式化的字符串列表。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 格式化后的字符串。 |

**示例：**

```ts
const lf = new Intl.ListFormat("en-US");
console.info(lf.format(["Apple", "Banana", "Orange"])); // "Apple, Banana, and Orange"

const lfShort = new Intl.ListFormat("en-US", { style: "short" });
console.info(lfShort.format(["Apple", "Banana"])); // "Apple & Banana"
```

### formatToParts

formatToParts(list: Iterable\<string>): Array\<FormatToPartsResult>

将列表格式化为片段数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| list | Iterable\<string> | 是 | 待格式化的字符串列表。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Array\<[FormatToPartsResult](#formattopartsresult)> | 格式化后的片段数组。 |

**示例：**

```ts
const lf = new Intl.ListFormat("en-US");
const parts = lf.formatToParts(["Apple", "Banana", "Orange"]);
// [{"type":"element","value":"Apple"},{"type":"literal","value":", "},{"type":"element","value":"Banana"},{"type":"literal","value":", and "},{"type":"element","value":"Orange"}]
console.info(JSON.stringify(parts));
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | string[], options?: ListFormatLocaleMatcher): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 是 | 待检查的区域标签或区域标签数组。 |
| options | [ListFormatLocaleMatcher](#listformatlocalematcher) | 否 | 区域匹配策略；默认为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.ListFormat.supportedLocalesOf(["en-US"]);
console.info(supported.length); // 1
console.info(supported.join()); // "en-US"

supported = Intl.ListFormat.supportedLocalesOf(["en-US", "zh-CN"], "lookup");
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,zh-CN"
```

## LocaleOptions

export interface LocaleOptions

Locale构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| baseName | string | 否 | 是 | 基础名称，由语言、书写系统和地区组成，如`'zh-Hans-CN'`；默认从语言标签解析。 |
| language | string | 否 | 是 | 语言标签，ISO 639标准，如`'zh'`、`'en'`；默认从系统区域获取。 |
| calendar | string | 否 | 是 | 日历类型，如`'gregory'`、`'chinese'`、`'islamic'`、`'hebrew'`等；默认为`''`。 |
| caseFirst | string | 否 | 是 | 大小写排列顺序，取值包括：`'upper'`：大写排前面，`'lower'`：小写排前面，`'false'`：使用区域默认的大小写排序规则；默认为`undefined`。 |
| numeric | boolean | 否 | 是 | 是否使用数字排序，`true`表示使用数字排序，`false`表示不使用数字排序；默认为`false`。 |
| collation | string | 否 | 是 | 排序规则，如`'pinyin'`（拼音排序）、`'stroke'`（笔画排序）、`'phonebk'`（电话本风格排序）等；默认为`undefined`。 |
| hourCycle | string | 否 | 是 | 小时周期，取值包括：`'h11'`表示0~11小时制，`'h12'`表示1~12小时制，`'h23'`表示0~23小时制，`'h24'`表示1~24小时制；默认为`undefined`。 |
| numberingSystem | string | 否 | 是 | 数字系统，如`'latn'`（拉丁数字）、`'arab'`（阿拉伯数字）、`'hans'`（简体中文数字）等；默认为`undefined`。 |
| region | string | 否 | 是 | 地区代码，ISO 3166标准，如`'CN'`、`'US'`；默认为`undefined`。 |
| script | string | 否 | 是 | 书写系统，ISO 15924标准，如`'Hans'`（简体中文）、`'Latn'`（拉丁文）、`'Arab'`（阿拉伯文）等；默认为`undefined`。 |

## Locale

export class Locale implements LocaleOptions

区域标识符对象，用于解析和操作BCP 47语言标签。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| baseName | string \| undefined | 否 | 是 | 基础名称（语言-脚本-地区），如`'zh-Hans-CN'`；默认从语言标签解析。 |
| language | string \| undefined | 否 | 是 | 语言标签，ISO 639标准，如`'zh'`、`'en'`；默认从系统区域获取。 |
| calendar | string \| undefined | 否 | 是 | 日历类型，如`'gregory'`、`'chinese'`、`'islamic'`、`'hebrew'`等；默认为`''`。 |
| caseFirst | string \| undefined | 否 | 是 | 大小写排列顺序，取值包括：`'upper'`：大写排前面，`'lower'`：小写排前面，`'false'`：使用区域默认的大小写排序规则；默认为`undefined`。 |
| numeric | boolean \| undefined | 否 | 是 | 是否使用数字排序，`true`表示使用数字排序，`false`表示不使用数字排序；默认为`false`。 |
| collation | string \| undefined | 否 | 是 | 排序规则，如`'pinyin'`（拼音排序）、`'stroke'`（笔画排序）、`'phonebk'`（电话本风格排序）等；默认为`undefined`。 |
| hourCycle | string \| undefined | 否 | 是 | 小时周期，取值包括：`'h11'`表示0~11小时制，`'h12'`表示1~12小时制，`'h23'`表示0~23小时制，`'h24'`表示1~24小时制；默认为`undefined`。 |
| numberingSystem | string \| undefined | 否 | 是 | 数字系统，如`'latn'`（拉丁数字）、`'arab'`（阿拉伯数字）、`'hans'`（简体中文数字）等；默认为`undefined`。 |
| region | string \| undefined | 否 | 是 | 地区代码，ISO 3166标准，如`'CN'`、`'US'`；默认为`undefined`。 |
| script | string \| undefined | 否 | 是 | 书写系统，ISO 15924标准，如`'Hans'`（简体中文）、`'Latn'`（拉丁文）、`'Arab'`（阿拉伯文）等；默认为`undefined`。 |

### constructor

constructor(tag: BCP47LanguageTag | Locale, options?: LocaleOptions)

创建Locale对象。传入无效标签时抛出`RangeError`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| tag | BCP47LanguageTag \| [Locale](#locale) | 是 | BCP 47语言标签或Locale对象。 |
| options | [LocaleOptions](#localeoptions) | 否 | 区域选项；默认各属性取默认值。 |

**示例：**

```ts
let locale = new Intl.Locale("en-US");
console.info(locale.language!); // "en"
console.info(locale.region!); // "US"
console.info(locale.baseName!); // "en-US"

locale = new Intl.Locale("zh-Hans-CN");
console.info(locale.language!); // "zh"
console.info(locale.script!); // "Hans"

const localeWithOptions = new Intl.Locale("en-US", { hourCycle: "h24" });
console.info(localeWithOptions.hourCycle!); // "h24"
```

### maximize

maximize(): Locale

根据现有值获取最可能的语言、脚本和地区，返回新的Locale实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [Locale](#locale) | 添加了可能子标签的新Locale实例。 |

**示例：**

```ts
const locale = new Intl.Locale("en");
const maximized = locale.maximize();
console.info(maximized.toString()); // "en-Latn-US"（添加了最可能的脚本和地区）
console.info(maximized.language!); // "en"
console.info(maximized.script!); // "Latn"
console.info(maximized.region!); // "US"
```

### minimize

minimize(): Locale

移除maximize()会添加的信息，返回新的Locale实例。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [Locale](#locale) | 移除了多余子标签的新Locale实例。 |

**示例：**

```ts
const locale = new Intl.Locale("en-Latn-US");
const minimized = locale.minimize();
console.info(minimized.toString()); // "en"（移除了多余子标签）
console.info(minimized.language!); // "en"
console.info(minimized.script); // undefined
console.info(minimized.region); // undefined
```

### toString

toString(): BCP47LanguageTag

返回Locale的完整区域标识符字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| BCP47LanguageTag | 完整的区域标识符字符串。 |

**示例：**

```ts
const locale = new Intl.Locale("zh-Hans-CN-u-ca-chinese-nu-hanidec");
console.info(locale.toString()); // "zh-Hans-CN-u-ca-chinese-u-nu-hanidec"
console.info(locale.calendar!); // "chinese"
console.info(locale.numberingSystem!); // "hanidec"
```

## NumberRangeFormatPart

export class NumberRangeFormatPart

数字范围格式化片段。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | [NumberFormatPartTypes](#numberformatparttypes) | 否 | 否 | 片段类型。 |
| value | string | 否 | 否 | 片段值。 |
| source | 'startRange' \| 'endRange' \| 'shared' | 否 | 否 | 片段来源，`'startRange'`表示片段来自起始数字，`'endRange'`表示片段来自结束数字，`'shared'`表示片段为起始和结束数字共用。 |

### constructor

constructor(type: NumberFormatPartTypes, value: string, source: 'startRange' | 'endRange' | 'shared')

创建NumberRangeFormatPart对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| type | [NumberFormatPartTypes](#numberformatparttypes) | 是 | 片段类型。 |
| value | string | 是 | 片段值。 |
| source | 'startRange' \| 'endRange' \| 'shared' | 否 | 片段来源，`'startRange'`表示片段来自起始数字，`'endRange'`表示片段来自结束数字，`'shared'`表示片段为起始和结束数字共用。 |

**示例：**

```ts
// NumberRangeFormatPart通常由NumberFormat.formatRangeToParts()返回，也可手动构造
const part = new Intl.NumberRangeFormatPart("integer", "5", "endRange");
console.info(part.type); // "integer"
console.info(part.value); // "5"
console.info(part.source); // "endRange"
```

## NumberFormatPart

export class NumberFormatPart

数字格式化片段。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | [NumberFormatPartTypes](#numberformatparttypes) | 否 | 否 | 片段类型。 |
| value | string | 否 | 否 | 片段值，对应type的格式化结果字符串，如type为`'integer'`时value可能为`"1"`，type为`'decimal'`时value可能为`"."`。 |

### constructor

constructor(type: NumberFormatPartTypes, value: string)

创建NumberFormatPart对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| type | [NumberFormatPartTypes](#numberformatparttypes) | 是 | 片段类型。 |
| value | string | 是 | 片段值。 |

**示例：**

```ts
// NumberFormatPart通常由NumberFormat.formatToParts()返回，也可手动构造
const part = new Intl.NumberFormatPart("currency", "¥");
console.info(part.type); // "currency"
console.info(part.value); // "¥"
```

## NumberFormatOptions

export interface NumberFormatOptions

NumberFormat构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| compactDisplay | 'short' \| 'long' | 否 | 是 | 紧凑显示方式，仅在notation为`'compact'`时生效，`'short'`为短格式（如1K），`'long'`为长格式（如1 thousand）；默认为`'short'`。 |
| currency | string | 否 | 是 | 货币代码，ISO 4217标准，如`'CNY'`（人民币）、`'USD'`（美元）、`'EUR'`（欧元）。仅在style为`'currency'`时必填；默认为`undefined`。 |
| currencyDisplay | 'code' \| 'symbol' \| 'narrowSymbol' \| 'name' | 否 | 是 | 货币显示方式，仅在style为`'currency'`时生效，`'code'`为ISO货币代码（如USD），`'symbol'`为货币符号（如$），`'narrowSymbol'`为窄货币符号（如$而非US$），`'name'`为货币名称（如US dollar）；默认为`'symbol'`。 |
| currencySign | 'standard' \| 'accounting' | 否 | 是 | 货币符号方式，仅在style为`'currency'`时生效，`'standard'`为标准符号，`'accounting'`为会计符号（负数用括号表示，如($100)）；默认为`'standard'`。 |
| localeMatcher | 'lookup' \| 'best fit' | 否 | 是 | 区域匹配策略，`'lookup'`为确定性匹配（按BCP 47算法逐步查找），`'best fit'`为启发式匹配（选择最合适的区域）；默认为`'best fit'`。 |
| maximumFractionDigits | int | 否 | 是 | 最大小数位数，取值范围0~20；默认为`3`。 |
| maximumSignificantDigits | int | 否 | 是 | 最大有效位数，取值范围1~21；默认为`undefined`。 |
| minimumIntegerDigits | int | 否 | 是 | 最小整数位数，取值范围1~21；默认为`1`。 |
| minimumFractionDigits | int | 否 | 是 | 最小小数位数，取值范围0~20；默认为`0`。 |
| minimumSignificantDigits | int | 否 | 是 | 最小有效位数，取值范围1~21；默认为`undefined`。 |
| notation | 'standard' \| 'scientific' \| 'engineering' \| 'compact' | 否 | 是 | 数字表示法，`'standard'`为标准表示，`'scientific'`为科学计数法（如1E3），`'engineering'`为工程计数法（如10E2），`'compact'`为紧凑表示（如1K）；默认为`'standard'`。 |
| signDisplay | 'auto' \| 'never' \| 'always' \| 'exceptZero' | 否 | 是 | 符号显示方式，`'auto'`为仅负数显示符号，`'never'`为不显示符号，`'always'`为始终显示符号，`'exceptZero'`为除零外始终显示符号；默认为`'auto'`。 |
| style | 'decimal' \| 'percent' \| 'currency' \| 'unit' | 否 | 是 | 格式化样式，`'decimal'`为纯数字，`'percent'`为百分比，`'currency'`为货币，`'unit'`为单位；默认为`'decimal'`。 |
| unit | string | 否 | 是 | 单位标识，如`'meter'`（米）、`'kilometer'`（千米）、`'liter'`（升）。仅在style为`'unit'`时必填；默认为`undefined`。 |
| unitDisplay | 'short' \| 'long' \| 'narrow' | 否 | 是 | 单位显示方式，仅在style为`'unit'`时生效，`'short'`为短格式（如km），`'long'`为长格式（如kilometer），`'narrow'`为窄格式（如k）；默认为`'short'`。 |
| useGrouping | boolean | 否 | 是 | 是否使用分组分隔符，`true`表示使用分组分隔符（如1,000），`false`表示不使用（如1000）；默认为`true`。 |

## ResolvedNumberFormatOptions

export interface ResolvedNumberFormatOptions

NumberFormat解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| compactDisplay | 'short' \| 'long' | 否 | 是 | 紧凑显示方式，仅在notation为`'compact'`时存在，`'short'`为短格式（如1K），`'long'`为长格式（如1 thousand）；默认为`'short'`。 |
| currencySign | 'standard' \| 'accounting' | 否 | 是 | 货币符号方式，仅在style为`'currency'`时存在，`'standard'`为标准符号，`'accounting'`为会计符号（负数用括号表示，如($100)）；默认为`'standard'`。 |
| currency | string | 否 | 是 | 货币代码，仅在style为`'currency'`时存在，ISO 4217标准，如`'CNY'`（人民币）、`'USD'`（美元）、`'EUR'`（欧元）；默认为`undefined`。 |
| currencyDisplay | 'code' \| 'symbol' \| 'narrowSymbol' \| 'name' | 否 | 是 | 货币显示方式，仅在style为`'currency'`时存在，`'code'`为ISO货币代码（如USD），`'symbol'`为货币符号（如$），`'narrowSymbol'`为窄货币符号（如$而非US$），`'name'`为货币名称（如US dollar）；默认为`'symbol'`。 |
| locale | [Intl.BCP47LanguageTag](#bcp47languagetag) | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| maximumFractionDigits | int | 否 | 否 | 最大小数位数，取值范围0~20。 |
| maximumSignificantDigits | int | 否 | 是 | 最大有效位数，取值范围1~21；默认为`21`（当minimumSignificantDigits已设置时自动填充）。 |
| minimumFractionDigits | int | 否 | 否 | 最小小数位数，取值范围0~20。 |
| minimumIntegerDigits | int | 否 | 否 | 最小整数位数，取值范围1~21。 |
| minimumSignificantDigits | int | 否 | 是 | 最小有效位数，取值范围1~21；默认为`1`（当maximumSignificantDigits已设置时自动填充）。 |
| notation | 'standard' \| 'scientific' \| 'engineering' \| 'compact' | 否 | 是 | 数字表示法，`'standard'`为标准表示，`'scientific'`为科学计数法（如1E3），`'engineering'`为工程计数法（如10E2），`'compact'`为紧凑表示（如1K）；默认为`'standard'`。 |
| numberingSystem | string | 否 | 否 | 数字系统，如`'latn'`（拉丁数字）、`'arab'`（阿拉伯数字）、`'hans'`（简体中文数字）等。 |
| signDisplay | 'auto' \| 'never' \| 'always' \| 'exceptZero' | 否 | 是 | 符号显示方式，`'auto'`为仅负数显示符号，`'never'`为不显示符号，`'always'`为始终显示符号，`'exceptZero'`为除零外始终显示符号；默认为`'auto'`。 |
| style | 'decimal' \| 'percent' \| 'currency' \| 'unit' | 否 | 否 | 格式化样式，`'decimal'`为纯数字，`'percent'`为百分比，`'currency'`为货币，`'unit'`为单位。 |
| unit | string | 否 | 是 | 单位标识，仅在style为`'unit'`时存在，如`'meter'`（米）、`'kilometer'`（千米）、`'liter'`（升）；默认为`undefined`。 |
| unitDisplay | 'short' \| 'long' \| 'narrow' | 否 | 是 | 单位显示方式，仅在style为`'unit'`时存在，`'short'`为短格式（如km），`'long'`为长格式（如kilometer），`'narrow'`为窄格式（如k）；默认为`'short'`。 |
| useGrouping | boolean | 否 | 否 | 是否使用分组分隔符，`true`表示使用分组分隔符（如1,000），`false`表示不使用（如1000）。 |

## NumberFormat

export class NumberFormat

数字格式化器，用于区域敏感的数字格式化。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: Intl.BCP47LanguageTag | Intl.BCP47LanguageTag[], options?: NumberFormatOptions)

创建NumberFormat对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | Intl.BCP47LanguageTag \| Intl.BCP47LanguageTag[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [NumberFormatOptions](#numberformatoptions) | 否 | 数字格式化选项；默认各属性取默认值。 |

**示例：**

```ts
let nf = new Intl.NumberFormat("en-US");
console.info(nf.format(1234.56)); // "1,234.56"

nf = new Intl.NumberFormat("de-DE");
console.info(nf.format(1234.56)); // "1.234,56"

nf = new Intl.NumberFormat("en-US", { style: "percent" });
console.info(nf.format(0.85)); // "85%"

nf = new Intl.NumberFormat("ja-JP", { style: "currency", currency: "JPY" });
console.info(nf.format(1500)); // "￥1,500"
```

### format

format(value: double | bigint | long): string

格式化数字。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double \| bigint \| long | 是 | 待格式化的数字。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 格式化后的数字字符串。 |

**示例：**

```ts
let nf = new Intl.NumberFormat("en-US");
console.info(nf.format(1234.56)); // "1,234.56"

nf = new Intl.NumberFormat("en-US", { style: "currency", currency: "USD" });
console.info(nf.format(1234.56)); // "$1,234.56"

nf = new Intl.NumberFormat("en-US", { notation: "scientific" });
console.info(nf.format(1234)); // "1.234E3"
```

### formatRange

formatRange(start: double | bigint, end: double | bigint): string

格式化数字范围。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | double \| bigint | 是 | 范围起始值。 |
| end | double \| bigint | 是 | 范围结束值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 格式化后的数字范围字符串。 |

**示例：**

```ts
const nf = new Intl.NumberFormat("en-US", { style: "currency", currency: "USD" });
console.info(nf.formatRange(1.0, 5.0)); // "$1.00 – $5.00"
console.info(nf.formatRange(0, 100)); // "$0.00 – $100.00"
```

### formatRangeToParts

formatRangeToParts(start: double | bigint, end: double | bigint): NumberRangeFormatPart[]

将数字范围格式化为片段数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| start | double \| bigint | 是 | 范围起始值。 |
| end | double \| bigint | 是 | 范围结束值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [NumberRangeFormatPart](#numberrangeformatpart)[] | 格式化后的片段数组。 |

**示例：**

```ts
const nf = new Intl.NumberFormat("en-US", { style: "currency", currency: "USD" });
const parts = nf.formatRangeToParts(1.0, 5.0);
for (const part of parts) {
    console.info(part.source + ": " + part.type + "=" + part.value);
}
// startRange: currency=$
// startRange: integer=1
// startRange: decimal=.
// startRange: fraction=00
// shared: literal= – 
// endRange: currency=$
// endRange: integer=5
// endRange: decimal=.
// endRange: fraction=00
```

### formatToParts

formatToParts(value: double | bigint): NumberFormatPart[]

将数字格式化为片段数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double \| bigint | 是 | 待格式化的数字。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [NumberFormatPart](#numberformatpart)[] | 格式化后的片段数组。 |

**示例：**

```ts
const nf = new Intl.NumberFormat("en-US", { style: "currency", currency: "EUR" });
const parts = nf.formatToParts(1234.56);
for (const part of parts) {
    console.info(part.type + ": " + part.value);
}
// currency: €
// integer: 1
// group: ,
// integer: 234
// decimal: .
// fraction: 56
```

### resolvedOptions

resolvedOptions(): ResolvedNumberFormatOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedNumberFormatOptions](#resolvednumberformatoptions) | 解析后的选项。 |

**示例：**

```ts
const nf = new Intl.NumberFormat("en-US", { style: "currency", currency: "USD" });
const options = nf.resolvedOptions();
console.info(options.locale); // "en-US"
console.info(options.style); // "currency"
console.info(options.currency); // "USD"
console.info(options.numberingSystem); // "latn"
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | string[], options?: NumberFormatOptions): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 是 | 待检查的区域标签或区域标签数组。 |
| options | [NumberFormatOptions](#numberformatoptions) | 否 | 区域匹配选项；默认localeMatcher为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.NumberFormat.supportedLocalesOf(["en-US", "zh-CN"]);
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,zh-CN"

supported = Intl.NumberFormat.supportedLocalesOf(["fr-FR"], { localeMatcher: "lookup" });
console.info(supported.length); // 1
console.info(supported.join()); // "fr-FR"
```

## PluralRulesOptions

export interface PluralRulesOptions

PluralRules构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| localeMatcher | 'lookup' \| 'best fit' \| undefined | 否 | 是 | 区域匹配策略，`'lookup'`为确定性匹配（按BCP 47算法逐步查找），`'best fit'`为启发式匹配（选择最合适的区域）；默认为`'best fit'`。 |
| type | [PluralRuleType](#pluralruletype) \| undefined | 否 | 是 | 复数规则类型；默认为`'cardinal'`。 |
| minimumIntegerDigits | int \| undefined | 否 | 是 | 最小整数位数，取值范围1~21；默认为`1`。 |
| minimumFractionDigits | int \| undefined | 否 | 是 | 最小小数位数，取值范围0~20；默认为`0`。 |
| maximumFractionDigits | int \| undefined | 否 | 是 | 最大小数位数，取值范围0~20；默认为`3`。 |
| minimumSignificantDigits | int \| undefined | 否 | 是 | 最小有效位数，取值范围1~21；默认为`undefined`。 |
| maximumSignificantDigits | int \| undefined | 否 | 是 | 最大有效位数，取值范围1~21；默认为`undefined`。 |

## ResolvedPluralRulesOptions

export interface ResolvedPluralRulesOptions

PluralRules解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| locale | string | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| localeMatcher | 'lookup' \| 'best fit' | 否 | 否 | 区域匹配策略，`'lookup'`为确定性匹配（按BCP 47算法逐步查找），`'best fit'`为启发式匹配（选择最合适的区域）。 |
| type | [PluralRuleType](#pluralruletype) | 否 | 否 | 复数规则类型。 |
| minimumIntegerDigits | int | 否 | 否 | 最小整数位数，取值范围1~21。 |
| minimumFractionDigits | int | 否 | 否 | 最小小数位数，取值范围0~20。 |
| maximumFractionDigits | int | 否 | 否 | 最大小数位数，取值范围0~20。 |
| minimumSignificantDigits | int | 否 | 是 | 最小有效位数，取值范围1~21；默认为`1`（当maximumSignificantDigits已设置时自动填充）。 |
| maximumSignificantDigits | int | 否 | 是 | 最大有效位数，取值范围1~21；默认为`3`（当minimumSignificantDigits已设置时自动填充）。 |
| pluralCategories | FixedArray\<[LDMLPluralRule](#ldmlpluralrule)> | 否 | 否 | 支持的复数类别，包含该区域可用的复数类别，如`['zero', 'one', 'other']`。 |

## SupportedLocalesOfOptions

export interface SupportedLocalesOfOptions

区域匹配选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| localeMatcher | 'lookup' \| 'best fit' \| undefined | 否 | 是 | 区域匹配策略，`'lookup'`为确定性匹配（按BCP 47算法逐步查找），`'best fit'`为启发式匹配（选择最合适的区域）；默认为`'best fit'`。 |

## PluralRulesSelectOptions

export interface PluralRulesSelectOptions

PluralRules选择选项（内部使用）。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| locale | string | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| type | string | 否 | 否 | 复数规则类型，`'cardinal'`为基数（表示数量），`'ordinal'`为序数（表示顺序）。 |
| minimumIntegerDigits | int | 否 | 否 | 最小整数位数，取值范围1~21。 |
| minimumFractionDigits | int | 否 | 否 | 最小小数位数，取值范围0~20。 |
| maximumFractionDigits | int | 否 | 否 | 最大小数位数，取值范围0~20。 |
| minimumSignificantDigits | int | 否 | 否 | 最小有效位数，取值范围1~21。 |
| maximumSignificantDigits | int | 否 | 否 | 最大有效位数，取值范围1~21。 |

## PluralRules

export class PluralRules

复数规则判断器，用于确定数值对应的复数类别。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: string | FixedArray\<string>, options?: PluralRulesOptions)

创建PluralRules对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| FixedArray\<string> | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [PluralRulesOptions](#pluralrulesoptions) | 否 | 复数规则选项；默认各属性取默认值。 |

**示例：**

```ts
let pr = new Intl.PluralRules("en-US");
console.info(pr.select(1)); // "one"
console.info(pr.select(2)); // "other"

pr = new Intl.PluralRules("en-US", { type: "ordinal" });
console.info(pr.select(1)); // "one"
console.info(pr.select(2)); // "two"
console.info(pr.select(3)); // "few"
```

### resolvedOptions

resolvedOptions(): ResolvedPluralRulesOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedPluralRulesOptions](#resolvedpluralrulesoptions) | 解析后的选项。 |

**示例：**

```ts
const pr = new Intl.PluralRules("en-US");
const options = pr.resolvedOptions();
console.info(options.locale); // "en-US"
console.info(options.type); // "cardinal"
console.info(options.pluralCategories.length); // 2
console.info(options.pluralCategories.toString()); // "one,other"
```

### select

select(value: double): LDMLPluralRule

返回数值对应的复数类别。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double | 是 | 待判断的数值。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [LDMLPluralRule](#ldmlpluralrule) | 复数类别。 |

**示例：**

```ts
const pr = new Intl.PluralRules("en-US");
console.info(pr.select(1)); // "one"
console.info(pr.select(0)); // "other"
console.info(pr.select(2)); // "other"
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | FixedArray\<string> | Array\<string>, options?: SupportedLocalesOfOptions | PluralRulesOptions): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| FixedArray\<string> \| Array\<string> | 是 | 待检查的区域。 |
| options | [SupportedLocalesOfOptions](#supportedlocalesofoptions) \| [PluralRulesOptions](#pluralrulesoptions) | 否 | 区域匹配选项；默认localeMatcher为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.PluralRules.supportedLocalesOf(["en-US", "zh-CN"]);
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,zh-CN"

let options: Intl.SupportedLocalesOfOptions = { localeMatcher: "lookup" };
supported = Intl.PluralRules.supportedLocalesOf(["de-DE"], options);
console.info(supported.length); // 1
console.info(supported.join()); // "de-DE"
```

## ResolvedRelativeTimeFormatOptions

export interface ResolvedRelativeTimeFormatOptions

RelativeTimeFormat解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| locale | string | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| numberingSystem | string | 否 | 否 | 数字系统，如`'latn'`（拉丁数字）、`'arab'`（阿拉伯数字）、`'hans'`（简体中文数字）等。 |
| numeric | [RelativeTimeFormatNumeric](#relativetimeformatnumeric) | 否 | 否 | 数值显示方式。 |
| style | [RelativeTimeFormatStyle](#relativetimeformatstyle) | 否 | 否 | 格式样式。 |

## RelativeTimeFormatOptions

export interface RelativeTimeFormatOptions

RelativeTimeFormat构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| numeric | [RelativeTimeFormatNumeric](#relativetimeformatnumeric) | 否 | 是 | 数值显示方式；默认为`'always'`。 |
| style | [RelativeTimeFormatStyle](#relativetimeformatstyle) | 否 | 是 | 格式样式；默认为`'long'`。 |
| localeMatcher | [RelativeTimeFormatLocaleMatcher](#relativetimeformatlocalematcher) | 否 | 是 | 区域匹配策略；默认为`'best fit'`。 |

## RelativeTimeFormatPart

export interface RelativeTimeFormatPart

相对时间格式化片段。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | string | 否 | 否 | 片段类型，`'literal'`为连接词或分隔符，`'integer'`为数值部分。 |
| unit | [RelativeTimeFormatUnit](#relativetimeformatunit) | 否 | 是 | 时间单位；默认为`undefined`（type为`'literal'`时不存在）。 |
| value | string | 否 | 否 | 片段值，对应type的格式化结果字符串，如type为`'integer'`时value可能为`"1"`，type为`'literal'`时value可能为`" day ago"`。 |

## RelativeTimeFormat

export class RelativeTimeFormat

相对时间格式化器，用于区域敏感的相对时间格式化。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: string | string[], options?: RelativeTimeFormatOptions)

创建RelativeTimeFormat对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [RelativeTimeFormatOptions](#relativetimeformatoptions) | 否 | 相对时间格式化选项；默认各属性取默认值。 |

**示例：**

```ts
let rtf = new Intl.RelativeTimeFormat("en-US");
console.info(rtf.format(-1, "day")); // "1 day ago"

rtf = new Intl.RelativeTimeFormat("zh-CN");
console.info(rtf.format(3, "month")); // "3个月后"

rtf = new Intl.RelativeTimeFormat("en-US", { numeric: "auto" });
console.info(rtf.format(-1, "day")); // "yesterday"
```

### format

format(value: double, unit: RelativeTimeFormatUnit): string

格式化相对时间。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double | 是 | 数值。 |
| unit | [RelativeTimeFormatUnit](#relativetimeformatunit) | 是 | 时间单位。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string | 格式化后的相对时间字符串。 |

**示例：**

```ts
let rtf = new Intl.RelativeTimeFormat("en-US");
console.info(rtf.format(-1, "day")); // "1 day ago"

rtf = new Intl.RelativeTimeFormat("en-US", { numeric: "auto" });
console.info(rtf.format(-1, "day")); // "yesterday"

rtf = new Intl.RelativeTimeFormat("en-US", { style: "short" });
console.info(rtf.format(5, "minute")); // "in 5 min."
```

### formatToParts

formatToParts(value: double, unit: RelativeTimeFormatUnit): RelativeTimeFormatPart[]

将相对时间格式化为片段数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | double | 是 | 数值。 |
| unit | [RelativeTimeFormatUnit](#relativetimeformatunit) | 是 | 时间单位。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [RelativeTimeFormatPart](#relativetimeformatpart)[] | 格式化后的片段数组。 |

**示例：**

```ts
const rtf = new Intl.RelativeTimeFormat("en-US");
const parts = rtf.formatToParts(-1, "day");
for (const part of parts) {
    console.info(part.type + ": " + part.value); // literal: 1 day ago
}
```

### resolvedOptions

resolvedOptions(): ResolvedRelativeTimeFormatOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedRelativeTimeFormatOptions](#resolvedrelativetimeformatoptions) | 解析后的选项。 |

**示例：**

```ts
const rtf = new Intl.RelativeTimeFormat("en-US", { numeric: "auto", style: "long" });
const options = rtf.resolvedOptions();
console.info(options.locale); // "en-US"
console.info(options.numeric); // "auto"
console.info(options.style); // "long"
console.info(options.numberingSystem); // "latn"
```

### supportedLocalesOf

static supportedLocalesOf(locales: string | string[], options?: RelativeTimeFormatOptions): string[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | string \| string[] | 是 | 待检查的区域标签或区域标签数组。 |
| options | [RelativeTimeFormatOptions](#relativetimeformatoptions) | 否 | 区域匹配选项；默认localeMatcher为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| string[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.RelativeTimeFormat.supportedLocalesOf(["en-US"]);
console.info(supported.length); // 1
console.info(supported.join()); // "en-US"

supported = Intl.RelativeTimeFormat.supportedLocalesOf(["en-US", "ja-JP"]);
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,ja-JP"
```

## SegmentData

export interface SegmentData

分词片段数据。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| index | int | 否 | 否 | 片段在原文中的起始索引，从0开始。 |
| input | string | 否 | 否 | 原始输入文本。 |
| isWordLike | boolean \| undefined | 否 | 是 | 是否为词类片段，`true`表示该片段是一个词，`false`表示不是词，仅在granularity为`'word'`时有值；默认为`undefined`。 |
| segment | string | 否 | 否 | 片段文本，即从原文中分割出的子字符串。 |

## SegmenterOptions

export interface SegmenterOptions

Segmenter构造选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| localeMatcher | 'best fit' \| 'lookup' | 否 | 是 | 区域匹配策略，`'best fit'`为启发式匹配（选择最合适的区域），`'lookup'`为确定性匹配（按BCP 47算法逐步查找）；默认为`'best fit'`。 |
| granularity | 'grapheme' \| 'word' \| 'sentence' | 否 | 是 | 分词粒度，`'grapheme'`为字素粒度（按字符分割），`'word'`为词粒度（按词分割），`'sentence'`为句子粒度（按句分割）；默认为`'grapheme'`。 |

## ResolvedSegmenterOptions

export interface ResolvedSegmenterOptions

Segmenter解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| locale | string | 否 | 否 | 区域标签，BCP 47格式，如`'zh-CN'`、`'en-US'`。 |
| granularity | 'grapheme' \| 'word' \| 'sentence' | 否 | 否 | 分词粒度，`'grapheme'`为字素粒度（按字符分割），`'word'`为词粒度（按词分割），`'sentence'`为句子粒度（按句分割）。 |

## Segments

export class Segments implements IterableIterator\<SegmentData>

分词结果迭代器。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(parent: SegmentDataImpl[])

创建Segments对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| parent | SegmentDataImpl[] | 是 | 分词片段数据数组。 |

**示例：**

```ts
// 通常通过Segmenter.segment()获取Segments
const segmenter = new Intl.Segmenter("zh-CN", { granularity: "word" });
const segments = segmenter.segment("你好世界");
```

### $_iterator

$_iterator(): IterableIterator\<SegmentData>

返回迭代器对象本身，用于支持for-of遍历。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<[SegmentData](#segmentdata)> | 迭代器对象本身。 |

**示例：**

```ts
const segmenter = new Intl.Segmenter("en-US", { granularity: "word" });
const segments = segmenter.segment("Hello world");

// $_iterator()返回迭代器对象本身，可用于手动获取迭代器
const it = segments.$_iterator();
let result = it.next();
console.info(result.value!.segment); // "Hello"
```

### next

next(): IteratorResult\<SegmentData>

返回下一个分词片段。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IteratorResult\<[SegmentData](#segmentdata)> | 下一个分词片段。 |

**示例：**

```ts
const segmenter = new Intl.Segmenter("en-US", { granularity: "word" });

// 使用next()逐个获取
const it = segmenter.segment("Hello world");
let result = it.next();
console.info(result.value!.segment); // "Hello"
result = it.next();
console.info(result.value!.segment == " "); // true
result = it.next();
console.info(result.value!.segment); // "world"
```

## Segmenter

export class Segmenter

分词器，用于区域敏感的文本分词。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(locales?: BCP47LanguageTag | BCP47LanguageTag[], options?: SegmenterOptions)

创建Segmenter对象。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | BCP47LanguageTag \| BCP47LanguageTag[] | 否 | 区域标签或区域标签数组；默认为系统区域。 |
| options | [SegmenterOptions](#segmenteroptions) | 否 | 分词选项；默认各属性取默认值。 |

**示例：**

```ts
let segmenter = new Intl.Segmenter("en-US");
const segments = segmenter.segment("Hello");
let res = new Array<string>();
for (const seg of segments) {
    res.push(seg.segment);
}
console.info(res.join("-")); // "H-e-l-l-o"

res = new Array<string>();
segmenter = new Intl.Segmenter("zh-CN", { granularity: "word" });
const zhSegments = segmenter.segment("你好世界");
for (const seg of zhSegments) {
    res.push(seg.segment);
}
console.info(res.join("-")); // "你好-世界"
```

### segment

segment(doc: string): Segments

对文本进行分词。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| doc | string | 是 | 待分词的文本。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [Segments](#segments) | 分词结果迭代器。 |

**示例：**

```ts
const segmenter = new Intl.Segmenter("en-US", { granularity: "word" });
const segments = segmenter.segment("Hello, world!");
let res = new Array<string>();
for (const seg of segments) {
    res.push(seg.segment);
    res.push(seg.isWordLike!.toString());
}
console.info(res.join("-")); // Hello-true-,-false- -false-world-true-!-false
```

### resolvedOptions

resolvedOptions(): ResolvedSegmenterOptions

返回解析后的选项。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| [ResolvedSegmenterOptions](#resolvedsegmenteroptions) | 解析后的选项。 |

**示例：**

```ts
const segmenter = new Intl.Segmenter("ja-JP", { granularity: "sentence" });
const options = segmenter.resolvedOptions();
console.info(options.locale); // "ja-JP"
console.info(options.granularity); // "sentence"
```

### supportedLocalesOf

static supportedLocalesOf(locales: BCP47LanguageTag | BCP47LanguageTag[], options?: SegmenterOptions): BCP47LanguageTag[]

返回支持的区域列表。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| locales | BCP47LanguageTag \| BCP47LanguageTag[] | 是 | 待检查的区域标签或区域标签数组。 |
| options | [SegmenterOptions](#segmenteroptions) | 否 | 区域匹配选项；默认options.localeMatcher为`'best fit'`。 |

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| BCP47LanguageTag[] | 支持的区域标签数组。 |

**示例：**

```ts
let supported = Intl.Segmenter.supportedLocalesOf(["en-US", "zh-CN"]);
console.info(supported.length); // 2
console.info(supported.join()); // "en-US,zh-CN"

supported = Intl.Segmenter.supportedLocalesOf(["ja-JP"], { localeMatcher: "lookup" });
console.info(supported.length); // 1
console.info(supported.join()); // "ja-JP"
```
