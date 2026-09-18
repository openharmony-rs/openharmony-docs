# CalendarManager

Before calling any of the following APIs to manage the calendar, you must use [getCalendarManager()](arkts-calendar-calendarmanager-getcalendarmanager-f.md) to obtain a **CalendarManager** object first.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## createCalendar

```TypeScript
createCalendar(calendarAccount: CalendarAccount): Promise<Calendar>
```

Creates a Calendar object based on the calendar account information. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | Yes | Calendar account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)&gt; | Promise used to return the created Calendar object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

const calendarAccount: calendarManager.CalendarAccount = {
  name: 'CreateMyCalendarByCallBack',
  type: calendarManager.CalendarType.LOCAL
};
try {
  calendarMgr?.createCalendar(calendarAccount, (err: BusinessError, data: calendarManager.Calendar) => {
    if (err) {
      console.error(`Failed to create calendar. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeeded in creating calendar, data -> ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  // Check whether the permission is granted or whether the parameters are correct.
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

const calendarAccount: calendarManager.CalendarAccount = {
  name: 'CreateMyCalendarByPromise',
  type: calendarManager.CalendarType.LOCAL,
  displayName : 'MyApplication'
};
calendarMgr?.createCalendar(calendarAccount).then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in creating calendar data->${JSON.stringify(data)}`);
}).catch((error : BusinessError) => {
  // Check whether the permission is granted or whether the parameters are correct.
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
});
```

## createCalendar

```TypeScript
createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void
```

Creates a Calendar object based on the calendar account information. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | Yes | Calendar account information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)&gt; | Yes | Callback used to return the created Calendar object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

See [createCalendar](#createcalendar)

## deleteCalendar

```TypeScript
deleteCalendar(calendar: Calendar): Promise<void>
```

Deletes a specified Calendar object. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| calendar | [Calendar](arkts-calendar-calendarmanager-calendar-i.md) | Yes | Calendar object to delete. The default account cannot be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

const calendarAccount: calendarManager.CalendarAccount = {
  name: 'DeleteMyCalendarByCallBack',
  type: calendarManager.CalendarType.LOCAL
};
calendarMgr?.createCalendar(calendarAccount).then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in creating calendar, data -> ${JSON.stringify(data)}`);
  calendarMgr?.getCalendar(calendarAccount, (err: BusinessError, data: calendarManager.Calendar) => {
    if (err) {
      console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
      calendarMgr?.deleteCalendar(data, (err1: BusinessError) => {
        if (err1) {
          // Check whether the parameters are correct.
          console.error(`Failed to delete calendar. Code: ${err1.code}, message: ${err1.message}`);
        } else {
          console.info('Succeeded in deleting calendar');
        }
      });
    }
  });
}).catch((error: BusinessError) => {
  // Check whether the permission is granted or whether the parameters are correct.
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
})
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

const calendarAccount: calendarManager.CalendarAccount = {
  name: 'DeleteMyCalendarByPromise',
  type: calendarManager.CalendarType.LOCAL
};
calendarMgr?.createCalendar(calendarAccount).then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in creating calendar, data -> ${JSON.stringify(data)}`);
  calendarMgr?.getCalendar(calendarAccount).then((data: calendarManager.Calendar) => {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendarMgr?.deleteCalendar(data).then(() => {
      console.info('Succeeded in deleting calendar');
    }).catch((err: BusinessError) => {
      // Check whether the parameters are correct.
      console.error(`Failed to delete calendar. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    // Check whether the permission is granted or whether the parameters are correct.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((error: BusinessError) => {
  // Check whether the permission is granted or whether the parameters are correct.
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
})
```

## deleteCalendar

```TypeScript
deleteCalendar(calendar: Calendar, callback: AsyncCallback<void>): void
```

Deletes a specified Calendar object. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.WRITE_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| calendar | [Calendar](arkts-calendar-calendarmanager-calendar-i.md) | Yes | Calendar object to delete. The default account cannot be deleted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Asynchronous callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

See [deleteCalendar](#deletecalendar)

## editEvent

```TypeScript
editEvent(event: Event): Promise<number>
```

Edits an event on the event creation page, with no event ID specified in **Event**. The **instanceStartTime**, **instanceEndTime**, **identifier**, **attendee**, **service**, **isLunar**, and **timeZone** attributes cannot be set. Important events cannot be added either. This API uses a promise to return the result.

Events created using this API can be obtained and modified by the system calendar. Third-party applications can obtain and modify the events after they requested the **READ_WHOLE_CALENDAR** permission and the **WRITE_WHOLE_CALENDAR** permission, respectively.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-calendar-calendarmanager-event-i.md) | Yes | **Event** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the event ID. The event ID is the unique identifier of an event and is the auto-increment primary key of the database. If the event creation fails, no value is returned; if the value is less than **0**, the event creation is canceled; if the value is greater than **0**, the event creation is successful. The return value cannot be **0** |

**Examples**

```TypeScript
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

const date = new Date();
const event: calendarManager.Event = {
  title: 'title',
  type: calendarManager.EventType.NORMAL,
  startTime: date.getTime(),
  endTime: date.getTime() + 60 * 60 * 1000
};
calendarMgr?.editEvent(event).then((eventId: number): void => {
  console.info(`create Event id = ${eventId}`);
});
```

## getAllCalendars

```TypeScript
getAllCalendars(): Promise<Calendar[]>
```

Obtains the created and default Calendar objects of the current application. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)[]&gt; | Promise used to return an array of obtained Calendar objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getAllCalendars((err: BusinessError, data: calendarManager.Calendar[]) => {
  if (err) {
    console.error(`Failed to get all calendars. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting all calendars, data -> ${JSON.stringify(data)}`);
    data.forEach((calendar) => {
      const account = calendar.getAccount();
      console.info(`account -> ${JSON.stringify(account)}`);
    })
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getAllCalendars().then((data: calendarManager.Calendar[]) => {
  console.info(`Succeeded in getting all calendars, data -> ${JSON.stringify(data)}`);
  data.forEach((calendar) => {
    const account = calendar.getAccount();
    console.info(`account -> ${JSON.stringify(account)}`);
  })
}).catch((err: BusinessError) => {
  // Check whether the permission has been successfully applied for.
  console.error(`Failed to get all calendars. Code: ${err.code}, message: ${err.message}`);
  
});
```

## getAllCalendars

```TypeScript
getAllCalendars(callback: AsyncCallback<Calendar[]>): void
```

Obtains the created and default Calendar objects of the current application. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)[]&gt; | Yes | Callback used to return an array of the obtained Calendar objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

See [getAllCalendars](#getallcalendars)

## getCalendar

```TypeScript
getCalendar(calendarAccount?: CalendarAccount): Promise<Calendar>
```

Obtains the default or specified Calendar object. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | No | Calendar account information, which is used to obtain a specified Calendar object. If this parameter is not set, the default Calendar object is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900003](../errorcode-calendarManager.md#23900003-specified-account-not-found) | The specified account was not found.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // Check whether the permission is granted or whether the parameters are correct.
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

const calendarAccount: calendarManager.CalendarAccount = {
  name: 'MyCalendar',
  type: calendarManager.CalendarType.LOCAL
};
calendarMgr?.createCalendar(calendarAccount).then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in creating calendar, data -> ${JSON.stringify(data)}`);
  calendarMgr?.getCalendar(calendarAccount, (err: BusinessError, data: calendarManager.Calendar) => {
    if (err) {
      console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
      // Check whether the permission is granted or whether the parameters are correct.
    } else {
      console.info(`Succeeded in getting calendar data -> ${JSON.stringify(data)}`);
    }
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
  // Check whether the permission is granted or whether the parameters are correct.
})
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Configure the EntryAbility file based on the sample code in calendarManager.getCalendarManager.
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getCalendar().then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  // Check whether the permission has been successfully applied for.
  console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
});
```

## getCalendar

```TypeScript
getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void
```

Obtains a specified Calendar object. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | Yes | Calendar account information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)&gt; | Yes | Callback used to return the obtained Calendar object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900003](../errorcode-calendarManager.md#23900003-specified-account-not-found) | The specified account was not found.<br>**Applicable version:** 23 and later |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

See [getCalendar](#getcalendar)

## getCalendar

```TypeScript
getCalendar(callback: AsyncCallback<Calendar>): void
```

Obtains the default Calendar object, which is created when the data storage runs for the first time. This API uses an asynchronous callback to return the result. You can call this API instead of createCalendar() to use the default calendar for a new event.

**Since:** 10

**Required permissions:** 
- API version 21 and later: ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR
- API versions 10 to 20: ohos.permission.READ_CALENDAR

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Calendar](arkts-calendar-calendarmanager-calendar-i.md)&gt; | Yes | Callback used to return the obtained Calendar object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [23900004](../errorcode-calendarManager.md#23900004-internal-program-error) | Internal program errors. Possible causes:<br>1. dataShare database execution error; <br>2. null pointer error; <br>3. Data parsing error.<br>**Applicable version:** 23 and later |

**Examples**

See [getCalendar](#getcalendar)
