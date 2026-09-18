# EventService

Describes the event service.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## description

```TypeScript
description?: string
```

Description of the service, with a maximum of 5,000 characters. If this parameter is not specified, the default value is an empty string.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: ServiceType
```

Service type.

**Type:** [ServiceType](arkts-calendar-calendarmanager-servicetype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## uri

```TypeScript
uri: string
```

Service URI, in the DeepLink format. The URI can then redirect the user to the corresponding third-party application page. The value is a string with a maximum of 5,000 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData
