# SymbolDateTimeFormat

提供自定义时间日期符号的能力。继承自 [Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)， 支持 [Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat) 的方法。

**继承/实现关系：** SymbolDateTimeFormat extends [Intl.DateTimeFormat](../../apis-localization-kit/arkts-apis/arkts-localization-intl-datetimeformat-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-i18n-export class SymbolDateTimeFormat--><!--Device-i18n-export class SymbolDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## constructor

```TypeScript
public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)
```

创建使用自定义符号的时间日期格式化对象。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)--><!--Device-SymbolDateTimeFormat-public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |
| options | [SymbolDateTimeFormatOptions](arkts-na-i18n-symboldatetimeformatoptions-i.md) | 否 | 自定义符号时间日期格式化的配置项。默认值：区域对象默认的符号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## parse

```TypeScript
public parse(text: string, lenientMode: boolean): long
```

解析本地化时间日期字符串，返回对应的时间戳。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public parse(text: string, lenientMode: boolean): long--><!--Device-SymbolDateTimeFormat-public parse(text: string, lenientMode: boolean): long-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待解析的本地化时间日期字符串。 |
| lenientMode | boolean | 是 | 是否采用宽松模式，true表示采用宽松模式，false表示不采用宽松模式。 <br>宽松模式下，能够处理不符合常规逻辑的时间日期值，如"5月32日"会自动转换成"6月1日"进行解析。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 时间日期字符串解析后对应的时间戳，单位为毫秒（ms）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## resolvedOptions

```TypeScript
public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions
```

解析自定义时间日期符号的配置项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolDateTimeFormat-public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions--><!--Device-SymbolDateTimeFormat-public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ResolvedSymbolDateTimeFormatOptions](arkts-na-i18n-resolvedsymboldatetimeformatoptions-i.md) | 自定义符号时间日期格式化对象配置项的解析结果。 |

