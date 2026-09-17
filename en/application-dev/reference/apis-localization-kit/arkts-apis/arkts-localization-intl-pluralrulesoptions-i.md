# PluralRulesOptions

Defines the options for creating a **PluralRules** object. Since API version 9, the **PluralRulesOptions** attribute is changed from mandatory to optional.

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#options)

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## localeMatcher

```TypeScript
localeMatcher?: string
```

Locale matching algorithm. The value can be **lookup** or **best fit**.

The default value is **best fit**.

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.localeMatcher](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#localematcher)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## maximumFractionDigits

```TypeScript
maximumFractionDigits?: number
```

Maximum number of digits in the fraction part of a number. The value ranges from **1** to **21**.

The default value is **3**.

**Type:** number

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.maximumFractionDigits](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#maximumfractiondigits)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## maximumSignificantDigits

```TypeScript
maximumSignificantDigits?: number
```

Maximum number of the least significant digits. The value ranges from **1** to **21**.

The default value is **21**.

**Type:** number

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.maximumSignificantDigits](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#maximumsignificantdigits)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## minimumFractionDigits

```TypeScript
minimumFractionDigits?: number
```

Minimum number of digits in the fraction part of a number. The value ranges from **0** to **20**.

The default value is **0**.

**Type:** number

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.minimumFractionDigits](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#minimumfractiondigits)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## minimumIntegerDigits

```TypeScript
minimumIntegerDigits?: number
```

Minimum number of digits allowed in the integer part of a number. The value ranges from **1** to **21**.

The default value is **1**.

**Type:** number

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.minimumIntegerDigits](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#minimumintegerdigits)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## minimumSignificantDigits

```TypeScript
minimumSignificantDigits?: number
```

Minimum number of the least significant digits. The value ranges from **1** to **21**.

The default value is **1**.

**Type:** number

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.minimumSignificantDigits](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#minimumsignificantdigits)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## type

```TypeScript
type?: string
```

Collation type. The value can be **cardinal** or **ordinal**.

The default value is **cardinal**.

The value **cardinal** indicates a cardinal number and the value **ordinal** indicates an ordinal number.

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.PluralRulesOptions.type](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/PluralRules/PluralRules#type)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n
