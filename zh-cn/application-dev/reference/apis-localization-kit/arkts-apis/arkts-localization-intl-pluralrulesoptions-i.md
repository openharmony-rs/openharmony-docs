# PluralRulesOptions

创建单复数对象时可设置的配置项。从API version 9开始，PluralRulesOptions的属性由必填改为可选。

**起始版本：** 8

**废弃版本：** 20

**替代接口：** options)

<!--Device-intl-export interface PluralRulesOptions--><!--Device-intl-export interface PluralRulesOptions-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## localeMatcher

```TypeScript
localeMatcher?: string
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.localeMatcher替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

区域匹配算法，取值包括："best fit", "lookup"。

默认值：best fit。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** localematcher)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-localeMatcher?: string--><!--Device-PluralRulesOptions-localeMatcher?: string-End-->

**系统能力：** SystemCapability.Global.I18n

## maximumFractionDigits

```TypeScript
maximumFractionDigits?: number
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.maximumFractionDigits替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

表示要使用的最大分数位数，取值范围：[1, 21]，小于1时取值为1，大于21时取值为21。

默认值：3。

**类型：** number

**起始版本：** 8

**废弃版本：** 20

**替代接口：** maximumfractiondigits)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-maximumFractionDigits?: int--><!--Device-PluralRulesOptions-maximumFractionDigits?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## maximumSignificantDigits

```TypeScript
maximumSignificantDigits?: number
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.maximumSignificantDigits替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

表示要使用的最大有效位数，取值范围：[1, 21]，小于1时取值为1，大于21时取值为21。

默认值：21。

**类型：** number

**起始版本：** 8

**废弃版本：** 20

**替代接口：** maximumsignificantdigits)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-maximumSignificantDigits?: int--><!--Device-PluralRulesOptions-maximumSignificantDigits?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## minimumFractionDigits

```TypeScript
minimumFractionDigits?: number
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.minimumFractionDigits替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

表示要使用的最小分数位数，取值范围：[0, 20]，小于0时取值为0，大于20时取值为20。

默认值：0。

**类型：** number

**起始版本：** 8

**废弃版本：** 20

**替代接口：** minimumfractiondigits)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-minimumFractionDigits?: int--><!--Device-PluralRulesOptions-minimumFractionDigits?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## minimumIntegerDigits

```TypeScript
minimumIntegerDigits?: number
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.minimumIntegerDigits替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

表示要使用的最小整数位数，取值范围：[1, 21]，小于1时取值为1，大于21时取值为21。

默认值：1。

**类型：** number

**起始版本：** 8

**废弃版本：** 20

**替代接口：** minimumintegerdigits)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-minimumIntegerDigits?: int--><!--Device-PluralRulesOptions-minimumIntegerDigits?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## minimumSignificantDigits

```TypeScript
minimumSignificantDigits?: number
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.minimumSignificantDigits替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

表示要使用的最小有效位数，取值范围：[1, 21]，小于1时取值为1，大于21时取值为21。

默认值：1。

**类型：** number

**起始版本：** 8

**废弃版本：** 20

**替代接口：** minimumsignificantdigits)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-minimumSignificantDigits?: int--><!--Device-PluralRulesOptions-minimumSignificantDigits?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## type

```TypeScript
type?: string
```

从API version 8开始支持，从API version 20开始废弃，建议使用Intl.PluralRulesOptions.type替代，用法参考[Intl.PluralRules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)。

排序的类型，取值包括："cardinal", "ordinal",

默认值：cardinal。

- cardinal：基数词，ordinal：序数词。

**类型：** string

**起始版本：** 8

**废弃版本：** 20

**替代接口：** type)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PluralRulesOptions-type?: string--><!--Device-PluralRulesOptions-type?: string-End-->

**系统能力：** SystemCapability.Global.I18n

