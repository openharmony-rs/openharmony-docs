# getSimpleDateTimeFormatByPattern

## getSimpleDateTimeFormatByPattern

```TypeScript
export function getSimpleDateTimeFormatByPattern(pattern: string, locale?: Intl.Locale): SimpleDateTimeFormat
```

通过模式字符串获取SimpleDateTimeFormat对象。与[getSimpleDateTimeFormatBySkeleton](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-getsimpledatetimeformatbyskeleton-f.md#getSimpleDateTimeFormatBySkeleton)接 口获取的对象在格式化后显示差异请参考[SimpleDateTimeFormat.format](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-simpledatetimeformat-c.md#format)的示例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getSimpleDateTimeFormatByPattern(pattern: string, locale?: Intl.Locale): SimpleDateTimeFormat--><!--Device-i18n-export function getSimpleDateTimeFormatByPattern(pattern: string, locale?: Intl.Locale): SimpleDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pattern | string | 是 | 合法的模式字符串，支持 [日期字段符号表](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table)中Field Patterns值的自由组合。同 时，pattern支持传入自定义文本，文本内容以`''`标识。 |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleDateTimeFormat](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-simpledatetimeformat-c.md) | SimpleDateTimeFormat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

