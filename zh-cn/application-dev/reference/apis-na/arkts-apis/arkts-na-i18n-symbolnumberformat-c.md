# SymbolNumberFormat

提供自定义数字符号的能力。继承自 [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat)， 支持 [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat) 的方法。

**继承/实现关系：** SymbolNumberFormat extends [Intl.NumberFormat](../../apis-localization-kit/arkts-apis/arkts-localization-intl-numberformat-c.md#NumberFormat)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-i18n-export class SymbolNumberFormat--><!--Device-i18n-export class SymbolNumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
public constructor(locale?: Intl.Locale, options?: SymbolNumberFormatOptions)
```

创建使用自定义符号的数字格式化对象。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public constructor(locale?: Intl.Locale, options?: SymbolNumberFormatOptions)--><!--Device-SymbolNumberFormat-public constructor(locale?: Intl.Locale, options?: SymbolNumberFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |
| options | [SymbolNumberFormatOptions](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-symbolnumberformatoptions-i.md) | 否 | 自定义数字格式化符号的配置项。默认值：区域默认的符号。 |

## parse

```TypeScript
public parse(text: string, lenientMode: boolean): double
```

解析本地化数字字符串，返回对应的数字。无法正确解析使用自定义符号的本地化数字字符串。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public parse(text: string, lenientMode: boolean): double--><!--Device-SymbolNumberFormat-public parse(text: string, lenientMode: boolean): double-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待解析的本地化数字字符串。 |
| lenientMode | boolean | 是 | 是否采用宽松模式，true表示采用宽松模式，false表示不采用宽松模式。 &lt;br&gt;宽松模式下，能够识别错误的千分符，如"1,23,456"可以正确解析为"123456"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 本地化数字字符串解析后的数字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## resolvedOptions

```TypeScript
public resolvedOptions(): ResolvedSymbolNumberFormatOptions
```

解析自定义数字符号的配置项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolNumberFormat-public resolvedOptions(): ResolvedSymbolNumberFormatOptions--><!--Device-SymbolNumberFormat-public resolvedOptions(): ResolvedSymbolNumberFormatOptions-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ResolvedSymbolNumberFormatOptions](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-resolvedsymbolnumberformatoptions-i.md) | 自定义符号数字格式化对象配置项的解析结果。 |

