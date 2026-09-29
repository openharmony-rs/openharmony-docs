# EventService

```TypeScript
export interface EventService
```

Describes the event service.

**Since:** 10

<!--Device-calendarManager-export interface EventService--><!--Device-calendarManager-export interface EventService-End-->

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

<!--Device-EventService-description?: string--><!--Device-EventService-description?: string-End-->

**System capability:** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: ServiceType
```

Service type.

**Type:** [ServiceType](arkts-calendar-calendarmanager-servicetype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EventService-type: ServiceType--><!--Device-EventService-type: ServiceType-End-->

**System capability:** SystemCapability.Applications.CalendarData

## uri

```TypeScript
uri: string
```

Service URI, in the DeepLink format. The URI can then redirect the user to the corresponding third-party application page. The value is a string with a maximum of 5,000 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EventService-uri: string--><!--Device-EventService-uri: string-End-->

**System capability:** SystemCapability.Applications.CalendarData
