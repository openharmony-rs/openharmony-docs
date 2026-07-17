# SymbolDateTimeFormat

提供自定义时间日期符号的能力。继承自[Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)，支持[Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)的方法。

**继承/实现关系：** SymbolDateTimeFormat extends [Intl.DateTimeFormat](Intl.DateTimeFormat)

**起始版本：** 26.0.0

<!--Device-i18n-export class SymbolDateTimeFormat extends Intl.DateTimeFormat--><!--Device-i18n-export class SymbolDateTimeFormat extends Intl.DateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)
```

创建使用自定义符号的时间日期格式化对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)--><!--Device-SymbolDateTimeFormat-public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |
| options | [SymbolDateTimeFormatOptions](arkts-localization-i18n-symboldatetimeformatoptions-i.md) | 否 | 自定义符号时间日期格式化的配置项。默认值：区域对象默认的符号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## format

```TypeScript
public format(date?: Date | number): string
```

对时间日期进行格式化，返回使用自定义符号的时间日期字符串。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public format(date?: Date | number): string--><!--Device-SymbolDateTimeFormat-public format(date?: Date | number): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date \| number | 否 | 时间日期对象或时间日期对应的毫秒值。时间日期对象中月份从0开始计数，0表示一月。<br>默认值：系统时间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 使用自定义符号的时间日期字符串。 |

## formatRange

```TypeScript
public formatRange(startDate: Date | number | bigint, endDate: Date | number | bigint): string
```

对时间日期范围进行格式化。自定义符号在该接口上暂不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public formatRange(startDate: Date | number | bigint, endDate: Date | number | bigint): string--><!--Device-SymbolDateTimeFormat-public formatRange(startDate: Date | number | bigint, endDate: Date | number | bigint): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startDate | Date \| number \| bigint | 是 | 时间日期对象或时间日期对应的毫秒值。时间日期对象中月份从0开始计数，0表示一月。 |
| endDate | Date \| number \| bigint | 是 | 时间日期对象或时间日期对应的毫秒值。时间日期对象中月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期范围字符串。 |

## formatRangeToParts

```TypeScript
public formatRangeToParts(startDate: Date | number | bigint, endDate: Date | number | bigint):
      Intl.DateTimeRangeFormatPart[]
```

把时间日期范围格式化成时间日期元素数组。自定义符号在该接口上暂不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public formatRangeToParts(startDate: Date | number | bigint, endDate: Date | number | bigint):
      Intl.DateTimeRangeFormatPart[]--><!--Device-SymbolDateTimeFormat-public formatRangeToParts(startDate: Date | number | bigint, endDate: Date | number | bigint):
      Intl.DateTimeRangeFormatPart[]-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startDate | Date \| number \| bigint | 是 | 时间日期对象或时间日期对应的毫秒值。时间日期对象中月份从0开始计数，0表示一月。 |
| endDate | Date \| number \| bigint | 是 | 时间日期对象或时间日期对应的毫秒值。时间日期对象中月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Intl.DateTimeRangeFormatPart[] | 时间日期范围元素数组。 |

## formatToParts

```TypeScript
public formatToParts(date?: Date | number): Intl.DateTimeFormatPart[]
```

对时间日期进行格式化，返回使用自定义符号的时间日期元素数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public formatToParts(date?: Date | number): Intl.DateTimeFormatPart[]--><!--Device-SymbolDateTimeFormat-public formatToParts(date?: Date | number): Intl.DateTimeFormatPart[]-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date \| number | 否 | 时间日期对象或时间日期对应的毫秒值。时间日期对象中月份从0开始计数，0表示一月。<br>默认值：系统时间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Intl.DateTimeFormatPart[] | 使用自定义符号的时间日期元素数组。 |

## parse

```TypeScript
public parse(text: string, lenientMode: boolean): number
```

解析本地化时间日期字符串，返回对应的时间戳。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public parse(text: string, lenientMode: boolean): number--><!--Device-SymbolDateTimeFormat-public parse(text: string, lenientMode: boolean): number-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待解析的本地化时间日期字符串。 |
| lenientMode | boolean | 是 | 是否采用宽松模式，true表示采用宽松模式，false表示不采用宽松模式。<br>宽松模式下，能够处理不符合常规逻辑的时间日期值，如"5月32日"会自动转换成"6月1日"进行解析。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 时间日期字符串解析后对应的时间戳，单位为毫秒（ms）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## resolvedOptions

```TypeScript
public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions
```

解析自定义时间日期符号的配置项。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions--><!--Device-SymbolDateTimeFormat-public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ResolvedSymbolDateTimeFormatOptions](arkts-localization-i18n-resolvedsymboldatetimeformatoptions-i.md) | 自定义符号时间日期格式化对象配置项的解析结果。 |

