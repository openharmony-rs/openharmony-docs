# SymbolDateTimeFormat

Provide a DateTime formatting interface that supports custom symbols. This interface formats date time values into strings with custom symbols, and can replace variable symbols in the formatted result with custom fixed symbols (e.g., replacing "2:23 PM" with "2:23 afternoon").

**Inheritance/Implementation:** SymbolDateTimeFormat extends Intl.DateTimeFormat

**Since:** 26.0.0

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
public constructor(locale?: Intl.Locale, options?: SymbolDateTimeFormatOptions)
```

A constructor used to create a SymbolDateTimeFormat object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | [Intl.Locale](arkts-localization-intl-locale-c.md) | No | Locale object used for formatting the date time value. The default value is the current system locale. |
| options | [SymbolDateTimeFormatOptions](arkts-localization-i18n-symboldatetimeformatoptions-i.md) | No | Indicates the symbols used to replace. The symbols that support replacement are "AM" and "PM". |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  timeStyle: 'short',
  amPMSymbol: ['AM', 'PM']
});
```

## format

```TypeScript
public format(date?: Date | number): string
```

Formats the date and time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date &#124; number | No | Date and time. Note: The month starts from 0. For example, 0 indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| string | The formatted date and time string. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  timeStyle: 'short',
  amPMSymbol: ['AM', 'PM']
});
let result = formatter.format(new Date(2026, 3, 26, 14, 20, 0)); // result = '2:20 AM'
```

## formatRange

```TypeScript
public formatRange(startDate: Date | number | bigint, endDate: Date | number | bigint): string
```

Formats date and time ranges.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startDate | Date &#124; number &#124; bigint | Yes | Start date and time, represented as a Date object or timestamp. Note: The month starts from 0. For example, 0 indicates January. |
| endDate | Date &#124; number &#124; bigint | Yes | End date and time, represented as a Date object or timestamp. Note: The month starts from 0. For example, 0 indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| string | A date string formatted based on the specified locale. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  timeStyle: 'short',
  amPMSymbol: ['AM', 'PM']
});
let startDate = new Date(2026, 3, 27, 14, 20, 0);
let endDate = new Date(2026, 3, 27, 18, 20, 0);
let result = formatter.formatRange(startDate, endDate); // result = '2:20 PM–6:20 PM'
```

## formatRangeToParts

```TypeScript
public formatRangeToParts(startDate: Date | number | bigint, endDate: Date | number | bigint):
      Intl.DateTimeRangeFormatPart[]
```

Formats a date time range to Parts.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startDate | Date &#124; number &#124; bigint | Yes | Start date and time, represented as a Date object or timestamp. Note: The month starts from 0. For example, 0 indicates January. |
| endDate | Date &#124; number &#124; bigint | Yes | End date and time, represented as a Date object or timestamp. Note: The month starts from 0. For example, 0 indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| [Intl.DateTimeRangeFormatPart](../../apis-default/arkts-apis/arkts-intl-datetimerangeformatpart-i.md)[] | Locale formatted DateTimeRangeFormatPart array. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  timeStyle: 'short',
  amPMSymbol: ['AM', 'PM']
});
let startDate = new Date(2026, 3, 27, 14, 20, 0);
let endDate = new Date(2026, 3, 27, 18, 20, 0);
let parts = formatter.formatRangeToParts(startDate, endDate); // parts[0].type = 'dayPeriod'
```

## formatToParts

```TypeScript
public formatToParts(date?: Date | number): Intl.DateTimeFormatPart[]
```

Formats a date to parts.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date &#124; number | No | Date or timestamp. Note: The month starts from 0. For example, 0 indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| [Intl.DateTimeFormatPart](../../apis-default/arkts-apis/arkts-intl-datetimeformatpart-i.md)[] | Locale formatted DateTimeFormatPart array. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  timeStyle: 'short',
  amPMSymbol: ['AM', 'PM']
});
let parts = formatter.formatToParts(new Date(2026, 3, 26, 14, 20, 0)); // parts[0].type = 'dayPeriod'
```

## parse

```TypeScript
public parse(text: string, lenientMode: boolean): number
```

Parse a date time localized string to Unix timestamp. Unix timestamp, indicating the number of milliseconds elapsed since 00:00:00 on January 1, 1970 GMT.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Localized string to be parse.<br>Text to be parsed |
| lenientMode | boolean | Yes | Indicates whether parsing allows any non-compliant localized strings. For example, "2023/02-25" is a invalid separator date string, it will parse failure when lenientMode is false, and will parse success with value (2023, 02, 25) when lenientMode is true. it's better set to false, ensure the data is not polluted.<br>Whether to use loose parsing rules |

**Return value:**

| Type | Description |
| --- | --- |
| number | Unix timestamp, which indicates the number of milliseconds that have elapsed since the Unix epoch. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  dateStyle: 'full'
});
let result = formatter.parse ('Sunday, May 10, 2026', false); // result = 1778342400000
```

## resolvedOptions

```TypeScript
public resolvedOptions(): ResolvedSymbolDateTimeFormatOptions
```

Obtains the options for creating a SymbolDateTimeFormat object. This will allow us to check the current config symbols.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| [ResolvedSymbolDateTimeFormatOptions](arkts-localization-i18n-resolvedsymboldatetimeformatoptions-i.md) | Symbol options for SymbolDateTimeFormat. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale = new Intl.Locale('zh-Hans-CN');
let formatter = new i18n.SymbolDateTimeFormat(locale, {
  timeStyle: 'short',
  amPMSymbol: ['AM', 'PM']
});
let options = formatter.resolvedOptions(); // options.timeStyle = 'short', options.amPMSymbol = ['AM', 'PM']
```
