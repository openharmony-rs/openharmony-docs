# getSimpleDateTimeFormatBySkeleton

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSimpleDateTimeFormatBySkeleton

```TypeScript
export function getSimpleDateTimeFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleDateTimeFormat
```

通过框架字符串获取SimpleDateTimeFormat对象。与[getSimpleDateTimeFormatByPattern](arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md#getsimpledatetimeformatbypattern-1)接口获取的对象在格式化后显示差异请参考[SimpleDateTimeFormat.format](arkts-localization-i18n-simpledatetimeformat-c.md#format-1)的示例。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getSimpleDateTimeFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleDateTimeFormat--><!--Device-i18n-export function getSimpleDateTimeFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skeleton | string | 是 | 合法的框架字符串，支持[日期字段符号表](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table)中Field Patterns值的自由组合。skeleton不支持传入自定义文本。 |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleDateTimeFormat](arkts-localization-i18n-simpledatetimeformat-c.md) | SimpleDateTimeFormat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |


## getSimpleDateTimeFormatBySkeleton

```TypeScript
export function getSimpleDateTimeFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleDateTimeFormat
```

通过框架字符串获取SimpleDateTimeFormat对象。与[getSimpleDateTimeFormatByPattern](arkts-localization-i18n-getsimpledatetimeformatbypattern-f.md#getsimpledatetimeformatbypattern-1)接口获取的对象在格式化后显示差异请参考[SimpleDateTimeFormat.format](arkts-localization-i18n-simpledatetimeformat-c.md#format-1)的示例。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** getSimpleDateTimeFormatBySkeleton(skeleton:

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getSimpleDateTimeFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleDateTimeFormat--><!--Device-i18n-export function getSimpleDateTimeFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skeleton | string | 是 | 合法的框架字符串，支持[日期字段符号表](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table)中Field Patterns值的自由组合。skeleton不支持传入自定义文本。 |
| locale | intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleDateTimeFormat](arkts-localization-i18n-simpledatetimeformat-c.md) | SimpleDateTimeFormat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

