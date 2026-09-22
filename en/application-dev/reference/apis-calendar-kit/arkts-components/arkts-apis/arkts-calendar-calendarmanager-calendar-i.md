# Calendar

```TypeScript
export interface Calendar
```

In the following API examples, you need to use [createCalendar()](arkts-calendar-calendarmanager-calendarmanager-i.md#createcalendar-1) or getCalendar() to obtain

a **Calendar** object before calling related APIs.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## addEvent

```TypeScript
addEvent(event: Event): Promise<number>
```

Adds an event, with no event ID, instanceStartTime, and instanceEndTime specified in Event. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-calendar-calendarmanager-event-i.md) | Yes | Event object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the event ID. The ID is greater than 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const event: calendarManager.Event = {
  type: calendarManager.EventType.NORMAL,
  startTime: date.getTime(),
  endTime: date.getTime() + 60 * 60 * 1000
};
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to addEvent. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="addevent-1"></a>

## addEvent

```TypeScript
addEvent(event: Event, callback: AsyncCallback<number>): void
```

Adds an event, with no event ID, instanceStartTime, and instanceEndTime specified in Event. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-calendar-calendarmanager-event-i.md) | Yes | Event object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the event ID. The event ID is the unique identifier of an event and is the auto-increment primary key of the database. If the value is less than 0, the event creation fails; if the value is greater than 0, the event creation succeeds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const event: calendarManager.Event = {
  type: calendarManager.EventType.NORMAL,
  startTime: date.getTime(),
  endTime: date.getTime() + 60 * 60 * 1000
};
calendarMgr?.getCalendar().then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
  calendar = data;
  calendar.addEvent(event, (err: BusinessError, data: number): void => {
    if (err) {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to addEvent. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }
  });
}).catch((err: BusinessError) => {
  // Check whether the permission has been successfully applied for.
  console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
});
```

## addEvents

```TypeScript
addEvents(events: Event[]): Promise<void>
```

Adds events in batches, with no event ID, instanceStartTime, and instanceEndTime specified in Event. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| events | [Event](arkts-calendar-calendarmanager-event-i.md)[] | Yes | Array of Event objects. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const events: calendarManager.Event[] = [
  {
    type: calendarManager.EventType.NORMAL,
    startTime: date.getTime(),
    endTime: date.getTime() + 60 * 60 * 1000
  },
  {
    type: calendarManager.EventType.NORMAL,
    startTime: date.getTime(),
    endTime: date.getTime() + 60 * 60 * 1000
  }
];
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    calendar.addEvents(events).then(() => {
      console.info('Succeeded in adding events');
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="addevents-1"></a>

## addEvents

```TypeScript
addEvents(events: Event[], callback: AsyncCallback<void>): void
```

Adds events in batches, with no event ID, instanceStartTime, and instanceEndTime specified in Event. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| events | [Event](arkts-calendar-calendarmanager-event-i.md)[] | Yes | Array of Event objects. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const events: calendarManager.Event[] = [
  {
    type: calendarManager.EventType.NORMAL,
    startTime: date.getTime(),
    endTime: date.getTime() + 60 * 60 * 1000
  },
  {
    type: calendarManager.EventType.NORMAL,
    startTime: date.getTime(),
    endTime: date.getTime() + 60 * 60 * 1000
  }
];
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    calendar.addEvents(events, (err: BusinessError) => {
      if (err) {
        // Check whether the permission is granted or whether the parameters are correct.
        console.error(`Failed to add events. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info('Succeeded in adding events');
      }
    });
  }
});
```

## deleteEvent

```TypeScript
deleteEvent(id: number): Promise<void>
```

Deletes an event with the specified ID. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Event ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
let id: number = 0;
const date = new Date();
const event: calendarManager.Event = {
  type: calendarManager.EventType.NORMAL,
  startTime: date.getTime(),
  endTime: date.getTime() + 60 * 60 * 1000
};
calendarMgr?.getCalendar(async (err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar data->${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      id = data;
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    calendar.deleteEvent(id).then(() => {
      console.info('Succeeded in deleting event');
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to delete event. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="deleteevent-1"></a>

## deleteEvent

```TypeScript
deleteEvent(id: number, callback: AsyncCallback<void>): void
```

Deletes an event with the specified ID. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Event ID, which is the unique identifier of an event. If the input event ID is an integer, the event is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
let id: number = 0;
const date = new Date();
const event: calendarManager.Event = {
  type: calendarManager.EventType.NORMAL,
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
    calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      id = data;
      calendar?.deleteEvent(id, (err: BusinessError) => {
        if (err) {
          // Check whether the parameters are correct.
          console.error(`Failed to delete event. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info('Succeeded in deleting event');
        }
      });
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

## deleteEvents

```TypeScript
deleteEvents(ids: number[]): Promise<void>
```

Deletes a batch of events with the specified IDs. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ids | number[] | Yes | Array of event IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
    calendar.deleteEvents([id1, id2]).then(() => {
      console.info('Succeeded in deleting events');
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to delete events. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="deleteevents-1"></a>

## deleteEvents

```TypeScript
deleteEvents(ids: number[], callback: AsyncCallback<void>): void
```

Deletes a batch of events with the specified IDs. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ids | number[] | Yes | Array of event IDs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

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
    calendar.deleteEvents([id1, id2], (err: BusinessError) => {
      if (err) {
        // Check whether the parameters are correct.
        console.error(`Failed to delete events. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info('Succeeded in deleting events');
      }
    });
  }
});
```

## getAccount

```TypeScript
getAccount(): CalendarAccount
```

Obtains the calendar account information.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Return value:**

| Type | Description |
| --- | --- |
| [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | Calendar account information. |

**Examples**

```TypeScript
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { BusinessError } from '@kit.BasicServicesKit';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    const account = calendar.getAccount();
    console.info(`succeeded in getting account, account -> ${JSON.stringify(account)}`);
  }
});
```

## getConfig

```TypeScript
getConfig(): CalendarConfig
```

Obtains the calendar configuration information.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Return value:**

| Type | Description |
| --- | --- |
| [CalendarConfig](arkts-calendar-calendarmanager-calendarconfig-i.md) | Calendar configuration information. |

**Examples**

```TypeScript
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { BusinessError } from '@kit.BasicServicesKit';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    const config = calendar.getConfig();
    console.info(`Succeeded in getting config, config -> ${JSON.stringify(config)}`);
  }
});
```

## getEvents

```TypeScript
getEvents(eventFilter?: EventFilter, eventKey?: (keyof Event)[]): Promise<Event[]>
```

Obtains all events in a calendar that match the filter criteria. This API uses a promise to return the result. If there is only one input parameter, the filter criteria, corresponding to the type EventFilter, must be set as the parameter. If no input parameter is specified, all events under the specified calendar account can be queried.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventFilter | [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | No | Filter criteria. |
| eventKey | (keyof Event)[] | No | Filter field. For versions earlier than API version 20, the default fields to be obtained include id, type, title, startTime, endTime, isAllDay, description, timeZone, location, service, attendee, and reminderTime if this parameter is left empty. Since API version 20, the default fields to be obtained include id, type, title, startTime, endTime, isAllDay, description, timeZone, location, service, attendee, reminderTime, and identifier if this parameter is left empty. The field is not returned if it is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Event](arkts-calendar-calendarmanager-event-i.md)[]&gt; | Promise used to return the result, which is an array of Event objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const event: calendarManager.Event = {
  title: 'MyEvent',
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
    await calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    // Perform fuzzy query based on MyEvent. If an event of the MyEvent1 type exists, the event can also be queried.
    const filter = calendarManager.EventFilter.filterByTitle('MyEvent');
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to get events. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="getevents-1"></a>

## getEvents

```TypeScript
getEvents(eventFilter: EventFilter, eventKey: (keyof Event)[], callback: AsyncCallback<Event[]>):void
```

Obtains all events in a calendar that match the filter criteria. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventFilter | [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | Yes | Filter criteria. |
| eventKey | (keyof Event)[] | Yes | Filter field. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Event](arkts-calendar-calendarmanager-event-i.md)[]&gt; | Yes | Callback used to return an array of events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

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
    const filter = calendarManager.EventFilter.filterById([id1, id2]);
    calendar.getEvents(filter, ['title', 'type', 'startTime', 'endTime'], (err: BusinessError, data: calendarManager.Event[]) => {
      if (err) {
        // Check whether the parameters are correct.
        console.error(`Failed to get events. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info(`Succeeded in getting events, data -> ${JSON.stringify(data)}`);
      }
    });
  }
});
```

<a id="getevents-2"></a>

## getEvents

```TypeScript
getEvents(callback: AsyncCallback<Event[]>):void
```

Obtains all events in the current calendar. This API uses an asynchronous callback to return the result.

For versions earlier than API version 20, the default fields to be obtained include id, type, title, startTime, endTime, isAllDay, description, timeZone, location, service, attendee, and reminderTime. Since API version 20, the default fields to be obtained include id, type, title, startTime, endTime, isAllDay, description, timeZone, location, service, attendee, reminderTime, and identifier. The field is not returned if it is empty.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Event](arkts-calendar-calendarmanager-event-i.md)[]&gt; | Yes | Callback used to return an array of events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar data -> ${JSON.stringify(data)}`);
    calendar = data;
    calendar.getEvents((err: BusinessError, data: calendarManager.Event[]) => {
      if (err) {
        console.error(`Failed to get events. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info(`Succeeded in getting events, data -> ${JSON.stringify(data)}`);
      }
    });
  }
});
```

## openEventEditPage

```TypeScript
openEventEditPage(id: number): Promise<void>
```

Obtains the event instance that meets the viewing or editing condition in a calendar based on the event ID. This API uses a promise to return the result.

This API can be used to view and edit calendar events in the system calendar.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The ID of the event to be edited. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23900001](../errorcode-calendarManager.md#23900001-parameter-value-error) | Parameter value error. |
| [23900005](../errorcode-calendarManager.md#23900005-event-not-editable) | This event cannot be edited. |

**Examples**

```TypeScript
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { BusinessError } from '@kit.BasicServicesKit';
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar: calendarManager.Calendar | undefined = undefined;
const date = new Date();
const event: calendarManager.Event = {
    title: 'MyEvent',
    type: calendarManager.EventType.NORMAL,
    startTime: date.getTime(),
    endTime: date.getTime() + 60 * 60 * 1000
  };
calendarMgr?.getCalendar(async (err: BusinessError, data: calendarManager.Calendar) => {
    if (err) {
      // Check whether the permission has been successfully applied for.
      console.error(`Failed to get calendar, Code is ${err.code}, message is ${err.message}`);
    } else {
      console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
      calendar = data;
      let eventId: number = 0;
      await calendar?.addEvent(event).then((dataId: number) => {
        console.info(`Succeeded in adding event id-> ${dataId}`);
        eventId = dataId;
      }).catch((err: BusinessError) => {
        // Check whether the permission is granted or whether the parameters are correct.
        console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
        return;
      });
      // Query by ID.
      const filterId = calendarManager.EventFilter.filterById([eventId]);
      calendar?.getEvents(filterId).then((data: calendarManager.Event[]) => {
        console.info(`Succeeded in getting event: ${JSON.stringify(data)}`);
      }).catch((err: BusinessError) => {
        // Check whether the parameters are correct, whether the passed ID exists, or whether there is any restriction on the permission.
        console.error(`Failed to get event, Code is ${err.code}, message is ${err.message}`);
        return;
      });
      calendar?.openEventEditPage(eventId).then(() => {
        console.info(`Succeeded in opening EventEditPage`);
      }).catch((err: BusinessError) => {
        // Check whether the passed ID exists, whether there is any restriction on the permission, or whether the event can be edited.
        console.error(`Failed to open eventeditpage, Code is ${err.code}, message is ${err.message}`);
      });
    }
 });
```

## queryEventInstances

```TypeScript
queryEventInstances(start: number, end: number, ids?: number[], eventKey?: (keyof Event)[]): Promise<Event[]>
```

Queries the event instance with a specified event key in a calendar. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 18 to 20: ohos.permission.READ_CALENDAR

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Start time of an event. The value is a 13-digit timestamp. |
| end | number | Yes | End time of an event. The value is a 13-digit timestamp. |
| ids | number[] | No | Array of event IDs to be queried, which can be empty or undefined. |
| eventKey | (keyof Event)[] | No | Event key for querying events. If this parameter is left empty, the default fields for filtering are id, title, startTime, endTime, instanceStartTime, instanceEndTime, isAllDay, description, timeZone, location, and service. The field is not returned if it is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Event](arkts-calendar-calendarmanager-event-i.md)[]&gt; | Promise used to return the result, which is an array of Event objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { BusinessError } from '@kit.BasicServicesKit';
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const event: calendarManager.Event = {
  title: 'MyEvent',
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
    await calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    calendar?.queryEventInstances(date.getTime(), date.getTime() + 60 * 60 * 1000, undefined,
      ['title', 'startTime', 'endTime', 'instanceStartTime', 'instanceEndTime']).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting event instances, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to get event instances. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

## setConfig

```TypeScript
setConfig(config: CalendarConfig): Promise<void>
```

Sets the calendar configuration information. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [CalendarConfig](arkts-calendar-calendarmanager-calendarconfig-i.md) | Yes | Calendar configuration information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23900001](../errorcode-calendarManager.md#23900001-parameter-value-error) | Parameter value error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const config: calendarManager.CalendarConfig = {
  enableReminder: true,
  color: '#aabbcc'
};
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    calendar.setConfig(config).then(() => {
      console.info(`Succeeded in setting config, data->${JSON.stringify(config)}`);
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to set config. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="setconfig-1"></a>

## setConfig

```TypeScript
setConfig(config: CalendarConfig, callback: AsyncCallback<void>): void
```

Sets the calendar configuration information. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [CalendarConfig](arkts-calendar-calendarmanager-calendarconfig-i.md) | Yes | Calendar configuration information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [23900001](../errorcode-calendarManager.md#23900001-parameter-value-error) | Parameter value error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const config: calendarManager.CalendarConfig = {
  enableReminder: true,
  color: '#aabbcc'
};
calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission has been successfully applied for.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    calendar.setConfig(config, (err: BusinessError) => {
      if (err) {
        // Check whether the permission is granted or whether the parameters are correct.
        console.error(`Failed to set config. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info(`Succeeded in setting config, config -> ${JSON.stringify(config)}`);
      }
    });
  }
});
```

## updateEvent

```TypeScript
updateEvent(event: Event): Promise<void>
```

Updates an event, with the ID of the updated event specified in Event. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-calendar-calendarmanager-event-i.md) | Yes | Event object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const oriEvent: calendarManager.Event = {
  title: 'update',
  type: calendarManager.EventType.NORMAL,
  description: 'updateEventTest',
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
    await calendar.addEvent(oriEvent).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      oriEvent.id = data;
      oriEvent.title = 'newUpdate';
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    calendar.updateEvent(oriEvent).then(() => {
      console.info(`Succeeded in updating event`);
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to update event. Code: ${err.code}, message: ${err.message}`);
    });
  }
});
```

<a id="updateevent-1"></a>

## updateEvent

```TypeScript
updateEvent(event: Event, callback: AsyncCallback<void>): void
```

Updates an event. The ID of the updated event must be specified in Event. If not, the event cannot be updated. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-calendar-calendarmanager-event-i.md) | Yes | Event object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of updateEvent. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

let calendar : calendarManager.Calendar | undefined = undefined;
const date = new Date();
const oriEvent: calendarManager.Event = {
  title: 'update',
  type: calendarManager.EventType.NORMAL,
  description: 'updateEventTest',
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
    await calendar.addEvent(oriEvent).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      oriEvent.id = data;
      oriEvent.title = 'newUpdate';
    }).catch((err: BusinessError) => {
      // Check whether the permission is granted or whether the parameters are correct.
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    calendar.updateEvent(oriEvent, (err: BusinessError) => {
      if (err) {
        // Check whether the parameters are correct.
        console.error(`Failed to update event. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info('Succeeded in updating event');
      }
    });
  }
});
```

## id

```TypeScript
readonly id: number
```

Calendar account ID, which is the unique identifier of a calendar account and is the auto-increment primary key of the database. If the value is less than 0, the account creation fails; if the value is greater than 0, the account creation succeeds.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData
