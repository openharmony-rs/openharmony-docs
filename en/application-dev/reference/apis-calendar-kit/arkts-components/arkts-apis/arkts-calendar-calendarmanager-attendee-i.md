# Attendee

Describes the attendees in a meeting.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## email

```TypeScript
email: string
```

Email address of the attendee, with a maximum of 5,000 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## name

```TypeScript
name: string
```

Name of the attendee, with a maximum of 5,000 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## role

```TypeScript
role?: AttendeeRole
```

Role of the Attendee.

**Type:** [AttendeeRole](arkts-calendar-calendarmanager-attendeerole-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## status

```TypeScript
status?: AttendeeStatus
```

Status of the attendee. If this parameter is not set, the default value is empty.

**Type:** [AttendeeStatus](arkts-calendar-calendarmanager-attendeestatus-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Applications.CalendarData

## type

```TypeScript
type?: AttendeeType
```

Type of the attendee. If this parameter is not set, the default value is empty.

**Type:** [AttendeeType](arkts-calendar-calendarmanager-attendeetype-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Applications.CalendarData
