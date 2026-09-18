# CalendarAccount

Describes the calendar account information.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## displayName

```TypeScript
displayName?: string
```

Account name displayed on the calendar application (defined by users). If this parameter is not specified, the default value is an empty string with a maximum of 64 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## name

```TypeScript
readonly name: string
```

Account name (defined by developers), with a maximum of 5,000 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: CalendarType
```

Account type.

**Type:** [CalendarType](arkts-calendar-calendarmanager-calendartype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData
