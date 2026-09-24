# DateTimeFormat

```TypeScript
export class DateTimeFormat
```

Performs date and time formatting.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { intl } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
constructor()
```

Creates a **DateTimeOptions** object for the specified locale.

**Since:** 8

**Deprecated since:** 20

**Substitutes:** [Intl.DateTimeFormat.constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a DateTimeFormat object using the current system locale ID.
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat();
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(locale: string | Array<string>, options?: DateTimeOptions)
```

Creates a **DateTimeOptions** object for the specified locale.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.DateTimeFormat.constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string &#124; Array&lt;string&gt; | Yes | Locale ID or locale ID array. If the input is a locale ID array, the first valid locale ID is used. |
| options | [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | No | Options for creating the **DateTimeOptions** object. If no options are set, the default values of **year**, **month**, and **day** are **numeric**. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

// Create a DateTimeFormat object with locale ID being zh-CN, dateStyle being full, and timeStyle being medium.
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('zh-CN', { dateStyle: 'full', timeStyle: 'medium' });

// Create a DateTimeFormat object with a locale ID array. The locale ID ban is invalid and therefore locale ID zh is used.
formatter = new intl.DateTimeFormat(['ban', 'zh'], { dateStyle: 'full', timeStyle: 'medium' });
```

## format

```TypeScript
format(date: Date): string
```

Formats the date and time.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.DateTimeFormat.format](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/format)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | Date and time. Note: The month starts from **0**. For example, **0** indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| string | A string containing the formatted date and time. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let date: Date = new Date(2021, 11, 17, 3, 24, 0); // The date and time is 2021.12.17 03:24:00.
// Create a DateTimeFormat object with the locale ID being en-GB.
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('en-GB');
let formattedDate: string = formatter.format(date); // formattedDate "17/12/2021"

// Create a DateTimeFormat object with locale ID being en-GB, dateStyle being full, and timeStyle being medium.
formatter = new intl.DateTimeFormat('en-GB', { dateStyle: 'full', timeStyle: 'medium' });
formattedDate = formatter.format(date); // formattedDate "Friday, 17 December 2021, 03:24:00"
```

## formatRange

```TypeScript
formatRange(startDate: Date, endDate: Date): string
```

Formats date and time ranges.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.DateTimeFormat.formatRange](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/formatRange)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startDate | Date | Yes | Start date and time. Note: The month starts from **0**. For example, **0** indicates January. |
| endDate | Date | Yes | End date and time. Note: The month starts from **0**. For example, **0** indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| string | A string containing the formatted date and time ranges. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let startDate: Date = new Date(2021, 11, 17, 3, 24, 0); // The date and time is 2021.12.17 03:24:00.
let endDate: Date = new Date(2021, 11, 18, 3, 24, 0);
// Create a DateTimeFormat object with the locale ID being en-GB.
let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('en-GB');
let formattedDateRange: string = formatter.formatRange(startDate, endDate); // formattedDateRange = '17/12/2021 - 18/12/2021'
```

## resolvedOptions

```TypeScript
resolvedOptions(): DateTimeOptions
```

Obtains the options for creating a **DateTimeOptions** object.

**Since:** 6

**Deprecated since:** 20

**Substitutes:** [Intl.DateTimeFormat.resolvedOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/resolvedOptions)

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [DateTimeOptions](arkts-localization-intl-datetimeoptions-i.md) | Options for the **DateTimeOptions** object. |

**Examples**

```TypeScript
import { intl } from '@kit.LocalizationKit';

let formatter: intl.DateTimeFormat = new intl.DateTimeFormat('en-GB', { dateStyle: 'full', timeStyle: 'medium' });
// Obtain the options of the DateTimeFormat object.
let options: intl.DateTimeOptions = formatter.resolvedOptions();
let dateStyle: string | undefined = options.dateStyle; // dateStyle = 'full'
let timeStyle: string | undefined = options.timeStyle; // timeStyle = 'medium'
```
