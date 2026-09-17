# EventFilter

Implements an event filter.

You can use [filterById()](#filterbyid), [filterByTime()](#filterbytime), [filterByTitle()](#filterbytitle) to obtain an event filter, and then pass the filter in getEvents() for filtering.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## filterById

```TypeScript
static filterById(ids: number[]): EventFilter
```

Defines a filter based on the event ID.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ids | number[] | Yes | An array of event IDs, where each event ID must be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | EventFilter object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
let id1: number = 0;
let id2: number = 0;
const date = new Date();
const event1: calendarManager.Event = {
  type: calendarManager.EventType.NORMAL,
  startTime: date.getTime(),
  endTime: date.getTime() + 60 * 60 * 1000
};
const event2: calendarManager.Event = {
  type: calendarManager.EventType.IMPORTANT,
  startTime: date.getTime(),
  endTime: date.getTime() + 60 * 60 * 1000
};
calendarMgr?.getCalendar(async (err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event1).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      id1 = data;
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    await calendar.addEvent(event2).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      id2 = data;
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    const filter = calendarManager.EventFilter.filterById([id1, id2]);
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events filter by id, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to filter by id. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

## filterByTime

```TypeScript
static filterByTime(start: number, end: number): EventFilter
```

Defines a filter based on the event time.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Start time. The value is a 13-digit timestamp. |
| end | number | Yes | End time. The value is a 13-digit timestamp. |

**Return value:**

| Type | Description |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | EventFilter object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const event1: calendarManager.Event = {
  type: calendarManager.EventType.NORMAL,
  startTime: 1686931200000,
  endTime: 1687017600000
};
const event2: calendarManager.Event = {
  type: calendarManager.EventType.IMPORTANT,
  startTime: 1686931200000,
  endTime: 1687017600000
};
calendarMgr?.getCalendar(async (err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event1).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    await calendar.addEvent(event2).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    const filter = calendarManager.EventFilter.filterByTime(1686931200000, 1687017600000);
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events filter by time, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to filter by time. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

## filterByTitle

```TypeScript
static filterByTitle(title: string): EventFilter
```

Filters events by event title. This API supports fuzzy match.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| title | string | Yes | Event title, with a maximum of 5,000 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | EventFilter object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const event: calendarManager.Event = {
  title: 'MyEvent',
  type: calendarManager.EventType.NORMAL,
  startTime: 1686931200000,
  endTime: 1687017600000
};
calendarMgr?.getCalendar(async (err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
       // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    const filter = calendarManager.EventFilter.filterByTitle('MyEvent');
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events filter by title, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to filter by title. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```
