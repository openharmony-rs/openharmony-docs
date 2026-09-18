# Event

Describes an **Event** object, including the event title, start time, and end time.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## attendee

```TypeScript
attendee?: Attendee[]
```

Attendees in a meeting. If this parameter is not set, the default null value is used.

**Type:** [Attendee](arkts-calendar-calendarmanager-attendee-i.md)[]

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## description

```TypeScript
description?: string
```

Event description, with a maximum of 5,000 characters. If this parameter is not specified, the default value is an empty string.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## endTime

```TypeScript
endTime: number
```

End time of an event. The value is a 13-digit timestamp. For an all-day event, this field is converted to timestamp corresponding to 00:00 of the specified date. When [getEvents()](arkts-calendar-calendarmanager-calendar-i.md#getevents) is called to query events, this field is queried by default.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## id

```TypeScript
id?: number
```

Event ID. This parameter does not need to be set in [addEvent()](arkts-calendar-calendarmanager-calendar-i.md#addevent) or [addEvents()](arkts-calendar-calendarmanager-calendar-i.md#addevents). This is an auto-increment field of the database, which has no default value. When [deleteEvent()](arkts-calendar-calendarmanager-calendar-i.md#deleteevent) or [deleteEvents()](arkts-calendar-calendarmanager-calendar-i.md#deleteevents) is called to delete an event, the value must be an integer. If an invalid value is passed, an error will be reported. When [getEvents()](arkts-calendar-calendarmanager-calendar-i.md#getevents) is called to query events, this field is queried by default.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## identifier

```TypeScript
identifier?: string
```

Unique ID of an event, with a maximum of 5,000 characters. If this parameter is not specified, the default value is null.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## instanceEndTime

```TypeScript
instanceEndTime?: number
```

End time of an event instance, which must be a 13-digit timestamp. The default value is undefined. This parameter is not required when [addEvent()](arkts-calendar-calendarmanager-calendar-i.md#addevent) or [addEvents()](arkts-calendar-calendarmanager-calendar-i.md#addevents) is called to create an event or [getEvents()](arkts-calendar-calendarmanager-calendar-i.md#getevents) is called to query an event.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Applications.CalendarData

## instanceStartTime

```TypeScript
instanceStartTime?: number
```

Start time of an event instance, which must be a 13-digit timestamp. The default value is undefined. This parameter is not required when [addEvent()](arkts-calendar-calendarmanager-calendar-i.md#addevent) or [addEvents()](arkts-calendar-calendarmanager-calendar-i.md#addevents) is called to create an event or [getEvents()](arkts-calendar-calendarmanager-calendar-i.md#getevents) is called to query an event.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Applications.CalendarData

## isAllDay

```TypeScript
isAllDay?: boolean
```

Whether the event is an all-day event. The value **true** means that the event is an all-day event, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## isLunar

```TypeScript
isLunar?: boolean
```

Unique ID of an event, with a maximum of 5,000 characters. If this parameter is not specified, the default value is null.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

## location

```TypeScript
location?: Location
```

Event location. If this parameter is not set, the default null value is used.

**Type:** [Location](arkts-calendar-calendarmanager-location-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## recurrenceRule

```TypeScript
recurrenceRule?: RecurrenceRule
```

Recurrence rule of an event. The event is a recurring event if this parameter is set; otherwise, the event is a non-recurring event.

**Type:** [RecurrenceRule](arkts-calendar-calendarmanager-recurrencerule-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## reminderTime

```TypeScript
reminderTime?: number[]
```

Reminder time of the event, in minutes. For example, if the value is 5, the reminder occurs 5 minutes before the event starts. If this parameter is not set, no reminder is set. A negative value indicates the delay time for sending a notification. For an all-day event, this parameter specifies the time offset in minutes before 9 a.m. on the event date. A negative value indicates the number of minutes after 9 a.m.

**Type:** number[]

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## service

```TypeScript
service?: EventService
```

&lt;!--RP1--&gt;Event service. If this parameter is not set, no one-click service is available. This function is not supported currently.&lt;!--RP1End--&gt;

**Type:** [EventService](arkts-calendar-calendarmanager-eventservice-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## startTime

```TypeScript
startTime: number
```

Start time of an event. The value is a 13-digit timestamp. For an all-day event, this field is converted to timestamp corresponding to 00:00 of the specified date. When [getEvents()](arkts-calendar-calendarmanager-calendar-i.md#getevents) is called to query events, this field is queried by default.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## timeZone

```TypeScript
timeZone?: string
```

Time zone of the event, with a maximum of 5,000 characters. If this parameter is not specified or set to an invalid value, the current time zone is used by default. If a different time zone is required, enter the corresponding time zone. You can call [systemDateTime.getTimezone()](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-systemdatetime-gettimezone-f.md) to obtain the current system time zone.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## title

```TypeScript
title?: string
```

Event title, with a maximum of 5,000 characters. If this parameter is not specified, the default value is an empty string.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: EventType
```

Event type.When [getEvents()](arkts-calendar-calendarmanager-calendar-i.md#getevents) is called to query events, this field is queried by default.

**Type:** [EventType](arkts-calendar-calendarmanager-eventtype-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData
