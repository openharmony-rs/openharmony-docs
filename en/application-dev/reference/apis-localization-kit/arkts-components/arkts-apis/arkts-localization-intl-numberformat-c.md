# NumberFormat

```TypeScript
export class NumberFormat
```

Provides the API for formatting number strings.

**Since:** 6

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor()
```

Creates a **NumberFormat** object for the current system locale.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a NumberFormat object using the current system locale ID.
let formatter: intl.NumberFormat = new intl.NumberFormat();
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: NumberOptions)
```

Creates a **NumberFormat** object based on the specified locale and options.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string &#124; Array&lt;string&gt; | Yes | Locale ID or locale ID array. If the input is a locale ID array, the first valid locale ID is used. |
| options | [NumberOptions](arkts-localization-intl-numberoptions-i.md) | No | Options for creating the **NumberFormat** object. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a NumberFormat object with locale ID being en-GB, style being decimal, and notation being scientific.
let formatter: intl.NumberFormat = new intl.NumberFormat('en-GB', { style: 'decimal', notation: 'scientific' });
```

## format

```TypeScript
format(num: number): string
```

Formats a number.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| num | number | Yes | Number to be formatted.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted number. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a NumberFormat object with a locale ID array. The locale ID en-GB is valid and therefore is used.
let formatter: intl.NumberFormat = new intl.NumberFormat(['en-GB', 'zh'], { style: 'decimal', notation: 'scientific' });
let formattedNumber: string = formatter.format(1223); // formattedNumber = 1.223E3
let options: intl.NumberOptions = {
  roundingPriority: 'lessPrecision',
  maximumFractionDigits: 3,
  maximumSignificantDigits: 3
}
formatter = new intl.NumberFormat('en', options);
let result: string = formatter.format(1.23456); // result = 1.23
```

## formatRange

```TypeScript
formatRange(startRange: number, endRange: number): string
```

Formats a number range.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startRange | number | Yes | Start number. |
| endRange | number | Yes | End number. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted number range. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let formatter: intl.NumberFormat = new intl.NumberFormat('en-US', { style: 'unit', unit: 'meter' });
let formattedRange: string = formatter.formatRange(0, 3); // formattedRange: 0–3 m
```

## resolvedOptions

```TypeScript
resolvedOptions(): NumberOptions
```

Obtains the options for creating a **NumberFormat** object.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [NumberOptions](arkts-localization-intl-numberoptions-i.md) | Options for creating the **NumberFormat** object. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let formatter: intl.NumberFormat = new intl.NumberFormat(['en-GB', 'zh'], { style: 'decimal', notation: 'scientific' });
// Obtain the options of the NumberFormat object.
let options: intl.NumberOptions = formatter.resolvedOptions();
let style: string | undefined = options.style; // style = 'decimal'
let notation: string | undefined = options.notation; // notation = 'scientific'
```
