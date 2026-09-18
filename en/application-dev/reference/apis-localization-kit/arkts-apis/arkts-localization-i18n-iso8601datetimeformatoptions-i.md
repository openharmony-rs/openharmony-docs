# ISO8601DateTimeFormatOptions

Represents optional configuration items for the ISO8601DateTimeFormat object. These options determine which elements need to be displayed after formatting and the corresponding format.

**Since:** 26.0.0

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## dateFormat

```TypeScript
dateFormat?: 'calendar' | 'ordinal' | 'week'
```

The ISO 8601 date format to format. The value can be: "calendar", the format is yyyy-MM-dd; "ordinal", the format is yyyy-DDD; "week", the format is YYYY-Www-e. Default value is "calendar".

**Type:** 'calendar' &#124; 'ordinal' &#124; 'week'

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## displayTimeZone

```TypeScript
displayTimeZone?: boolean
```

Check if need to show time zone part. Default value is true that show time zone.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## separatorStyle

```TypeScript
separatorStyle?: 'extended' | 'basic'
```

The date time separator style. The value can be: "extended": with -/:, "basic": compact mode. Default separator style is "extended".

**Type:** 'extended' &#124; 'basic'

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## timePrecision

```TypeScript
timePrecision?: 'dateOnly' | 'hours' | 'minutes' | 'seconds' | 'milliSeconds'
```

The ISO 8601 time precision to format. The value can be: "dateOnly", "hours", "minutes", "seconds","milliSeconds". Default value is "seconds".

**Type:** 'dateOnly' &#124; 'hours' &#124; 'minutes' &#124; 'seconds' &#124; 'milliSeconds'

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## timeZone

```TypeScript
timeZone?: TimeZone
```

TimeZone object used to format date, default value UTC.

**Type:** [TimeZone](arkts-localization-i18n-timezone-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n
