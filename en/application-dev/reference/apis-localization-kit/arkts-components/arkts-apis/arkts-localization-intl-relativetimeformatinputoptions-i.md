# RelativeTimeFormatInputOptions

Defines the configuration options for a **RelativeTimeFormat** object. Since API version 9, the attributes in **RelativeTimeFormatInputOptions** are optional.

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.RelativeTimeFormatOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/RelativeTimeFormat#options)

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

**Substitutes:** [Intl.RelativeTimeFormatOptions.localeMatcher](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/RelativeTimeFormat#localematcher)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## numeric

```TypeScript
numeric?: string
```

Format of the output result. It determines whether numeric values are used to represent relative dates or times in the formatting result. The value can be **always** or **auto**.

The default value is **always**.

For details about their display effects, see [Table 23](../../../reference/apis-localization-kit/js-apis-intl.md#appendix).

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.RelativeTimeFormatOptions.numeric](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/RelativeTimeFormat#numeric)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## style

```TypeScript
style?: string
```

Length of an internationalized message. The value can be **long**, **short**, or **narrow**.

The default value is **long**.

**Type:** string

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.RelativeTimeFormatOptions.style](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/RelativeTimeFormat#style)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n
