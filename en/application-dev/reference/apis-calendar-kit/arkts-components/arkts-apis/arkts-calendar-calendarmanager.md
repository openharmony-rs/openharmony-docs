# @ohos.calendarManager

The calendarManager module provides APIs for calendar and event management, including those for creating, deleting, modifying, and querying calendars and events.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getCalendarManager](arkts-calendar-calendarmanager-getcalendarmanager-f.md) | Obtains a CalendarManager object based on the context. |

### Classes

| Name | Description |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | Implements an event filter. |

### Interfaces

| Name | Description |
| --- | --- |
| [Attendee](arkts-calendar-calendarmanager-attendee-i.md) | Describes the attendees in a meeting. |
| [Calendar](arkts-calendar-calendarmanager-calendar-i.md) | In the following API examples, you need to use [createCalendar()](arkts-calendar-calendarmanager-calendarmanager-i.md#createcalendar) or getCalendar() to obtain |
| [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | Describes the calendar account information. |
| [CalendarConfig](arkts-calendar-calendarmanager-calendarconfig-i.md) | Describes the calendar configuration information. |
| [CalendarManager](arkts-calendar-calendarmanager-calendarmanager-i.md) | Before calling any of the following APIs to manage the calendar, you must use [getCalendarManager()](arkts-calendar-calendarmanager-getcalendarmanager-f.md) to obtain a **CalendarManager** object first. |
| [Event](arkts-calendar-calendarmanager-event-i.md) | Describes an **Event** object, including the event title, start time, and end time. |
| [EventService](arkts-calendar-calendarmanager-eventservice-i.md) | Describes the event service. |
| [Location](arkts-calendar-calendarmanager-location-i.md) | Describes the event location. |
| [RecurrenceRule](arkts-calendar-calendarmanager-recurrencerule-i.md) | Describes the recurrence rule of a recurring event. |

### Enums

| Name | Description |
| --- | --- |
| [AttendeeRole](arkts-calendar-calendarmanager-attendeerole-e.md) | Enumerates the attendee role types in a conference event. |
| [AttendeeStatus](arkts-calendar-calendarmanager-attendeestatus-e.md) | Enumerates the status types of an attendee. |
| [AttendeeType](arkts-calendar-calendarmanager-attendeetype-e.md) | Enumerates the types of attendees invited to a conference event. |
| [CalendarType](arkts-calendar-calendarmanager-calendartype-e.md) | Enumerates the account types. |
| [EventType](arkts-calendar-calendarmanager-eventtype-e.md) | Enumerates event types. |
| [RecurrenceFrequency](arkts-calendar-calendarmanager-recurrencefrequency-e.md) | Enumerates the types of the event recurrence rule. |
| [ServiceType](arkts-calendar-calendarmanager-servicetype-e.md) | Enumerates the event service types. |
