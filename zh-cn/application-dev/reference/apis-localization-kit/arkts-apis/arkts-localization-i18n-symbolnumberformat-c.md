# SymbolNumberFormat

提供自定义数字符号的能力。继承自[Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat)，支持[Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat)的方法。

**继承/实现关系：** SymbolNumberFormat implements [Intl.NumberFormat](arkts-localization-intl-numberformat-c.md)

**起始版本：** 26.0.0

<!--Device-i18n-export class SymbolNumberFormat implements Intl.NumberFormat--><!--Device-i18n-export class SymbolNumberFormat implements Intl.NumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
public constructor(locale?: Intl.Locale, options?: SymbolNumberFormatOptions)
```

创建使用自定义符号的数字格式化对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public constructor(locale?: Intl.Locale, options?: SymbolNumberFormatOptions)--><!--Device-SymbolNumberFormat-public constructor(locale?: Intl.Locale, options?: SymbolNumberFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |
| options | [SymbolNumberFormatOptions](arkts-localization-i18n-symbolnumberformatoptions-i.md) | 否 | 自定义数字格式化符号的配置项。默认值：区域默认的符号。 |

## format

```TypeScript
public format(value: number | bigint): string
```

对数字进行格式化，返回使用自定义符号的数字字符串。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public format(value: number | bigint): string--><!--Device-SymbolNumberFormat-public format(value: number | bigint): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| bigint | 是 | 待格式化的数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 使用自定义符号的数字字符串。 |

## formatRange

```TypeScript
public formatRange(startRange: number, endRange: number): string
```

对数字范围进行格式化，返回使用自定义符号的数字范围字符串。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public formatRange(startRange: number, endRange: number): string--><!--Device-SymbolNumberFormat-public formatRange(startRange: number, endRange: number): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startRange | number | 是 | 起始数字。 |
| endRange | number | 是 | 终止数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 使用自定义符号的数字范围字符串。 |

## formatRangeToParts

```TypeScript
public formatRangeToParts(startRange: number, endRange: number): Intl.NumberFormatPart[]
```

对数字范围进行格式化，返回使用自定义符号的数字元素数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public formatRangeToParts(startRange: number, endRange: number): Intl.NumberFormatPart[]--><!--Device-SymbolNumberFormat-public formatRangeToParts(startRange: number, endRange: number): Intl.NumberFormatPart[]-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startRange | number | 是 | 起始数字。 |
| endRange | number | 是 | 终止数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Intl.NumberFormatPart[] | 使用自定义符号的数字元素数组。 |

## formatToParts

```TypeScript
public formatToParts(value?: number | bigint): Intl.NumberFormatPart[]
```

对数字进行格式化，返回使用自定义符号的数字元素数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public formatToParts(value?: number | bigint): Intl.NumberFormatPart[]--><!--Device-SymbolNumberFormat-public formatToParts(value?: number | bigint): Intl.NumberFormatPart[]-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| bigint | 否 | 待格式化的数字。默认值：NaN。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Intl.NumberFormatPart[] | 使用自定义符号的数字元素数组。 |

## parse

```TypeScript
public parse(text: string, lenientMode: boolean): number
```

解析本地化数字字符串，返回对应的数字。无法正确解析使用自定义符号的本地化数字字符串。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public parse(text: string, lenientMode: boolean): number--><!--Device-SymbolNumberFormat-public parse(text: string, lenientMode: boolean): number-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待解析的本地化数字字符串。 |
| lenientMode | boolean | 是 | 是否采用宽松模式，true表示采用宽松模式，false表示不采用宽松模式。<br>宽松模式下，能够识别错误的千分符，如"1,23,456"可以正确解析为"123456"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 本地化数字字符串解析后的数字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## resolvedOptions

```TypeScript
public resolvedOptions(): ResolvedSymbolNumberFormatOptions
```

解析自定义数字符号的配置项。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public resolvedOptions(): ResolvedSymbolNumberFormatOptions--><!--Device-SymbolNumberFormat-public resolvedOptions(): ResolvedSymbolNumberFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ResolvedSymbolNumberFormatOptions](arkts-localization-i18n-resolvedsymbolnumberformatoptions-i.md) | 自定义符号数字格式化对象配置项的解析结果。 |

