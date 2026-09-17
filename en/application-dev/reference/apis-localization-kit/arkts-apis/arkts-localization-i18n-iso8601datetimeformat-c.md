# ISO8601DateTimeFormat

Provide a DateTime formatting interface which could format date to ISO 8601 standard string. [ISO8601](https://iso8601.com/).

**Since:** 26.0.0

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## constructor

```TypeScript
public constructor(options?: ISO8601DateTimeFormatOptions)
```

A constructor used to create a ISO8601DateTimeFormat object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ISO8601DateTimeFormatOptions](arkts-localization-i18n-iso8601datetimeformatoptions-i.md) | No | Options for creating a date formatting object that complies with ISO 8601. |

**Examples**

```TypeScript
let formatter = new i18n.ISO8601DateTimeFormat({
  dateFormat: 'calendar',
  timePrecision: 'minutes',
  separatorStyle: 'extended'
});
```

## format

```TypeScript
public format(date: Date): string
```

Formats a date to ISO 8601 formatted string.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | date to be formatted. Note: The month starts from 0. For example, 0 indicates January. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Date and time string that complies with ISO 8601. |

**Examples**

```TypeScript
let formatter = new i18n.ISO8601DateTimeFormat({
  dateFormat: 'calendar',
  timePrecision: 'minutes',
  separatorStyle: 'extended'
});
let result = formatter.format(new Date(2026, 2, 15, 12, 0, 0));
```
