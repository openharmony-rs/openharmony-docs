# 全球化子系统Changelog

## cl.global.1 接口错误码类型从string类型变更为number类型

**访问级别**

公共能力

**变更原因**

系统错误码类型默认为number类型，全球化接口的实现一直使用string类型。从API版本26.0.0开始，全球化新增接口的错误码类型变更为number类型。

**变更影响**

从API版本26.0.0开始，新增接口的错误码类型为number类型，此前版本接口的错误码类型仍为string类型。

**起始API Level**

26.0.0

**变更发生版本**

从OpenHarmony SDK 7.0.0.36开始。

**变更的接口/组件**
- i18n.ChineseCalendar.setChineseCalendarTime
- i18n.ChineseCalendar.checkLeapMonth
- i18n.TimeZone.setAppDefaultTimeZoneById
- i18n.Unicode.detectEncoding
- i18n.I18NUtil.setUnicodeWrappedBidiDirection
- i18n.I18NUtil.convertCanonicalLocaleIdentifier
- i18n.SymbolDateTimeFormat.constructor
- i18n.SymbolDateTimeFormat.format
- i18n.SymbolDateTimeFormat.formatToParts
- i18n.SymbolDateTimeFormat.formatRange
- i18n.SymbolDateTimeFormat.formatRangeToParts
- i18n.SymbolDateTimeFormat.parse
- i18n.SymbolNumberFormat.constructor
- i18n.SymbolNumberFormat.format
- i18n.SymbolNumberFormat.formatToParts
- i18n.SymbolNumberFormat.formatRange
- i18n.SymbolNumberFormat.formatRangeToParts
- i18n.SymbolNumberFormat.parse

**适配指导**

接口默认行为变更。请开发者确认此变更是否影响业务逻辑（如错误码类型判断），如有影响需进行适配。
