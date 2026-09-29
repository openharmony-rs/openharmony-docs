# Attendee

```TypeScript
export interface Attendee
```

Describes the attendees in a meeting.

**Since:** 10

<!--Device-calendarManager-export interface Attendee--><!--Device-calendarManager-export interface Attendee-End-->

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

<!--Device-Attendee-email: string--><!--Device-Attendee-email: string-End-->

**System capability:** SystemCapability.Applications.CalendarData

## name

```TypeScript
name: string
```

Name of the attendee, with a maximum of 5,000 characters.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Attendee-name: string--><!--Device-Attendee-name: string-End-->

**System capability:** SystemCapability.Applications.CalendarData

## role

```TypeScript
role?: AttendeeRole
```

Role of the Attendee.

**Type:** [AttendeeRole](arkts-calendar-calendarmanager-attendeerole-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Attendee-role?: AttendeeRole--><!--Device-Attendee-role?: AttendeeRole-End-->

**System capability:** SystemCapability.Applications.CalendarData

## status

```TypeScript
status?: AttendeeStatus
```

Status of the attendee. If this parameter is not set, the default value is empty.

**Type:** [AttendeeStatus](arkts-calendar-calendarmanager-attendeestatus-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Attendee-status?: AttendeeStatus--><!--Device-Attendee-status?: AttendeeStatus-End-->

**System capability:** SystemCapability.Applications.CalendarData

## type

```TypeScript
type?: AttendeeType
```

Type of the attendee. If this parameter is not set, the default value is empty.

**Type:** [AttendeeType](arkts-calendar-calendarmanager-attendeetype-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Attendee-type?: AttendeeType--><!--Device-Attendee-type?: AttendeeType-End-->

**System capability:** SystemCapability.Applications.CalendarData
