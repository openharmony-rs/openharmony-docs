# ChineseCalendarTime

Represents chinese calendar time element for the ChineseCalendar object.

**Since:** 26.0.0

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## cyclicalYear

```TypeScript
cyclicalYear: number
```

The cyclical year of date. If you need to convert between the chinese calendar and the Gregorian calendar, the year range must be set from 1 to 60. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## date

```TypeScript
date: number
```

Date of the chinese calendar time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## gregorianYear

```TypeScript
gregorianYear: number
```

The gregorian year of date. If you need to convert between the chinese calendar and the Gregorian calendar, the year range must be set from 1900 to 2100.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## hour

```TypeScript
hour?: number
```

Hour of the chinese calendar time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## isLeapMonth

```TypeScript
isLeapMonth?: boolean
```

Determines whether the input month is a leap month.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## minute

```TypeScript
minute?: number
```

Minute of the chinese calendar time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## month

```TypeScript
month: number
```

Month of the chinese calendar time. Note: The month starts from 0. For example, 0 indicates January.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

## second

```TypeScript
second?: number
```

Second of the chinese calendar time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n
