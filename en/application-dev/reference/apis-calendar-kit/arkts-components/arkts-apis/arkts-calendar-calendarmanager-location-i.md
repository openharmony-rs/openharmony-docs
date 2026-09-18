# Location

Describes the event location.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## latitude

```TypeScript
latitude?: number
```

Latitude of the location. The value range is [-90, 90]. The default value is **undefined**. If the value is out of the range, the map cannot be displayed properly.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## location

```TypeScript
location?: string
```

Location, with a maximum of 5,000 characters. If this parameter is not specified, the default value is an empty string.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## longitude

```TypeScript
longitude?: number
```

Longitude of the location. The value range is [-180, 180]. The default value is **undefined**. If the value is out of the range, the map cannot be displayed properly.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData
