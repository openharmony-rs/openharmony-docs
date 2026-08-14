# @ohos.i18n

本模块提供系统相关的以及增强的[国际化](../../../internationalization/i18n-l10n.md)能力，包括区域管理、电话号码处理、日历等，相关接口为 [ECMA 402](https://dev.ecma-international.org/publications-and-standards/standards/ecma-402/)标准中未定义的补充接口。 [国际化-Intl](../../apis-localization-kit/arkts-apis/arkts-intl.md#@ohos.intl(国际化-Intl))模块提供了ECMA 402标准定义的基础国际化接口，与本模块共同使用可提供完整的国际化能力。接口中使用的名词定义如下： - 模式字符串：由[Unicode日期字段符号](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table)和单引号包裹的自定义文本自由组 合而成的字符串。 - 框架字符串：由[Unicode日期字段符号](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table)自由组合而成的字符串，不支持自 定义文本。 > **说明：** > > - 本模块接口基于[CLDR](https://cldr.unicode.org)国际化数据库实现，随着CLDR标准的迭代演进，接口处理结果可能会相应调整。例如时间日期格式化接口，其返回值仅适用于界面展示场景，开发者请勿对返回格式 > 进行硬编码或假设性判断，否则可能导致版本兼容问题。其中，API version 12 对应[CLDR 42](https://cldr.unicode.org/downloads/cldr-42)版本，具体数据变更详情可查阅 > [CLDR官方文档](https://cldr.unicode.org/)。 > > - 从API version 11开始，本模块部分接口支持在ArkTS卡片中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace i18n--><!--Device-unnamed-declare namespace i18n-End-->

**系统能力：** SystemCapability.Global.I18n

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCalendar](arkts-na-i18n-getcalendar-f.md#getCalendar) | 获取指定区域和历法的日历对象。 |
| [getChineseCalendar](arkts-na-i18n-getchinesecalendar-f.md#getChineseCalendar) | 获取指定区域的农历对象。 |
| [getInstance](arkts-na-i18n-getinstance-f.md#getInstance) | 创建并返回IndexUtil对象。 |
| [getLineInstance](arkts-na-i18n-getlineinstance-f.md#getLineInstance) | 获取用于定位文本可换行点的BreakIterator对象。该对象内部维护一个换行迭代器，可以用于访问各个可换行点。 |
| [getSimpleDateTimeFormatByPattern](arkts-na-i18n-getsimpledatetimeformatbypattern-f.md#getSimpleDateTimeFormatByPattern) | 通过模式字符串获取SimpleDateTimeFormat对象。与[getSimpleDateTimeFormatBySkeleton](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-getsimpledatetimeformatbyskeleton-f.md#getSimpleDateTimeFormatBySkeleton)接 口获取的对象在格式化后显示差异请参考[SimpleDateTimeFormat.format](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-simpledatetimeformat-c.md#format)的示例。 |
| [getSimpleDateTimeFormatBySkeleton](arkts-na-i18n-getsimpledatetimeformatbyskeleton-f.md#getSimpleDateTimeFormatBySkeleton) | 通过框架字符串获取SimpleDateTimeFormat对象。与[getSimpleDateTimeFormatByPattern](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md#getSimpleDateTimeFormatByPattern)接口获 取的对象在格式化后显示差异请参考[SimpleDateTimeFormat.format](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-simpledatetimeformat-c.md#format)的示例。 |
| [getSimpleNumberFormatBySkeleton](arkts-na-i18n-getsimplenumberformatbyskeleton-f.md#getSimpleNumberFormatBySkeleton) | 通过框架字符串获取SimpleNumberFormat对象。 |
| [getTimeZone](arkts-na-i18n-gettimezone-f.md#getTimeZone) | 获取时区ID对应的时区对象。 |
| [isRTL](arkts-na-i18n-isrtl-f.md#isRTL) | 判断语言是否为镜像语言。在镜像语言下，UI界面需要[镜像显示](../../../internationalization/i18n-ui-design.md#界面镜像)。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AdvancedMeasureFormat](arkts-na-i18n-advancedmeasureformat-c.md) | 提供数字格式化能力，支持根据单位使用场景自动转换合适的单位。 |
| [BreakIterator](arkts-na-i18n-breakiterator-c.md) | 提供文本换行相关的能力，包括可换行点的获取、移动和识别等。 |
| [Calendar](arkts-na-i18n-calendar-c.md) | 提供历法相关的能力，包括历法名称获取和日期计算等。 |
| [ChineseCalendar](arkts-na-i18n-chinesecalendar-c.md) | 提供农历相关的能力，包括设置农历时间、判断指定年份某月是否存在闰月。 继承自[Calendar](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-calendar-c.md#Calendar)，支持[Calendar](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-calendar-c.md#Calendar)的方法。 |
| [EntityRecognizer](arkts-na-i18n-entityrecognizer-c.md) | 提供实体识别相关的能力，可以获取文本中实体的类型和起止位置。当前支持识别的实体包括电话号码和时间日期。 |
| [HolidayManager](arkts-na-i18n-holidaymanager-c.md) | 提供解析节假日数据的能力，包括节假日判断和指定年份节假日列表获取等。 |
| [I18NUtil](arkts-na-i18n-i18nutil-c.md) | 国际化工具类，提供单位转换、获取日期顺序、获取时段名称、区域匹配和路径本地化等能力。 |
| [ISO8601DateTimeFormat](arkts-na-i18n-iso8601datetimeformat-c.md) | 符合ISO 8601标准的日期格式化对象。 |
| [IndexUtil](arkts-na-i18n-indexutil-c.md) | 提供索引相关的能力，包括区域索引列表和文本索引值获取。 |
| [Normalizer](arkts-na-i18n-normalizer-c.md) | 提供文本标准化的能力。 |
| [PhoneNumberFormat](arkts-na-i18n-phonenumberformat-c.md) | 提供电话号码相关的能力，包括电话号码有效性判断、格式化和归属地获取。 |
| [SimpleDateTimeFormat](arkts-na-i18n-simpledatetimeformat-c.md) | 提供时间日期格式化的能力。 |
| [SimpleNumberFormat](arkts-na-i18n-simplenumberformat-c.md) | 基于框架字符串提供数字格式化的能力。 |
| [StyledDateTimeFormat](arkts-na-i18n-styleddatetimeformat-c.md) | 提供富文本时间日期格式化的能力。 |
| [StyledNumberFormat](arkts-na-i18n-stylednumberformat-c.md) | 提供富文本数字格式化的能力。 |
| [SymbolDateTimeFormat](arkts-na-i18n-symboldatetimeformat-c.md) | 提供自定义时间日期符号的能力。继承自 [Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)， 支持 [Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat) 的方法。 |
| [SymbolNumberFormat](arkts-na-i18n-symbolnumberformat-c.md) | 提供自定义数字符号的能力。继承自 [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat)， 支持 [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat) 的方法。 |
| [System](arkts-na-i18n-system-c.md) | 提供系统属性相关的能力，包括语言地区名称翻译、支持的语言地区列表获取和系统语言地区获取等。 |
| [TimeZone](arkts-na-i18n-timezone-c.md) | 提供时区相关的能力，包括时区名称翻译、偏移量获取和跳变规则获取等。 |
| [Transliterator](arkts-na-i18n-transliterator-c.md) | 提供文本音译相关的能力，包括音译支持范围获取和文本音译等。 |
| [Unicode](arkts-na-i18n-unicode-c.md) | 提供字符属性相关的能力，包括判断字符是否为空格、数字和字母等。 |
| [ZoneOffsetTransition](arkts-na-i18n-zoneoffsettransition-c.md) | 提供解析时区跳变规则的能力。 |
| [ZoneRules](arkts-na-i18n-zonerules-c.md) | 提供查询时区跳变规则的能力。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [System](arkts-na-i18n-system-c-sys.md) | 提供系统属性相关的能力，包括语言地区名称翻译、支持的语言地区列表获取和系统语言地区获取等。 |
| [SystemLocaleManager](arkts-na-i18n-systemlocalemanager-c-sys.md) | 提供语言、地区和时区信息排序的能力。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvancedMeasureFormatOptions](arkts-na-i18n-advancedmeasureformatoptions-i.md) | 创建数字格式化对象时的可选配置项。 |
| [ChineseCalendarTime](arkts-na-i18n-chinesecalendartime-i.md) | 农历时间对象。 |
| [EncodingInfo](arkts-na-i18n-encodinginfo-i.md) | 编码信息。 |
| [EntityInfoItem](arkts-na-i18n-entityinfoitem-i.md) | 实体信息属性。 |
| [HolidayInfoItem](arkts-na-i18n-holidayinfoitem-i.md) | 节假日信息。 |
| [HolidayLocalName](arkts-na-i18n-holidaylocalname-i.md) | 节假日名称在不同语言下的翻译。 |
| [ISO8601DateTimeFormatOptions](arkts-na-i18n-iso8601datetimeformatoptions-i.md) | 符合ISO 8601标准的日期格式化对象创建时的配置项。 |
| [PhoneNumberFormatOptions](arkts-na-i18n-phonenumberformatoptions-i.md) | 电话号码格式化时可设置的配置项。 |
| [ResolvedSymbolDateTimeFormatOptions](arkts-na-i18n-resolvedsymboldatetimeformatoptions-i.md) | 自定义符号时间日期格式化对象配置项的解析结果。继承自Intl.ResolvedDateTimeFormatOptions， 支持Intl.ResolvedDateTimeFormatOptions的所有配置项，并且功能与其一致。 |
| [ResolvedSymbolNumberFormatOptions](arkts-na-i18n-resolvedsymbolnumberformatoptions-i.md) | 自定义符号数字格式化对象配置项的解析结果。继承自Intl.ResolvedNumberFormatOptions， 支持Intl.ResolvedNumberFormatOptions的所有配置项，并且功能与其一致。 |
| [StyledDateTimeFormatOptions](arkts-na-i18n-styleddatetimeformatoptions-i.md) | 创建富文本显示的时间日期格式化对象时的可选配置项。 |
| [StyledNumberFormatOptions](arkts-na-i18n-stylednumberformatoptions-i.md) | 创建富文本显示的数字格式化对象时的可选配置项。 |
| [SymbolDateTimeFormatOptions](arkts-na-i18n-symboldatetimeformatoptions-i.md) | 创建自定义符号时间日期格式化对象时的可选配置项。继承自Intl.DateTimeFormatOptions， 支持Intl.DateTimeFormatOptions的所有配置项，并且功能与其一致。 |
| [SymbolNumberFormatOptions](arkts-na-i18n-symbolnumberformatoptions-i.md) | 创建自定义符号数字格式化对象时的可选配置项。继承自Intl.NumberFormatOptions， 支持Intl.NumberFormatOptions的所有配置项，并且功能与其一致。 |
| [UnitInfo](arkts-na-i18n-unitinfo-i.md) | 度量衡单位信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LocaleItem](arkts-na-i18n-localeitem-i-sys.md) | 语言或国家地区的组合信息。 |
| [SortOptions](arkts-na-i18n-sortoptions-i-sys.md) | 语言或国家地区排序选项。 |
| [TimeZoneCityItem](arkts-na-i18n-timezonecityitem-i-sys.md) | 时区城市的组合信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NormalizerMode](arkts-na-i18n-normalizermode-e.md) | 文本标准化范式的枚举。 |
| [TemperatureType](arkts-na-i18n-temperaturetype-e.md) | 温度单位的枚举。 |
| [UnitUsage](arkts-na-i18n-unitusage-e.md) | 单位格式化使用场景的枚举。 |
| [WeekDay](arkts-na-i18n-weekday-e.md) | 周起始日的枚举，取值范围为周一至周日。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SuggestionType](arkts-na-i18n-suggestiontype-e-sys.md) | 语言或国家地区的推荐类型。 |
<!--DelEnd-->

