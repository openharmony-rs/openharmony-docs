# CalendarManager

下列API示例中需先通过[getCalendarManager()](arkts-calendar-calendarmanager-getcalendarmanager-f.md#getcalendarmanager-1)方法获取CalendarManager对象，再通过此对象调用对应方法，进行Calendar的创建、删除、修改、查询等操作。

**起始版本：** 10

<!--Device-calendarManager-export interface CalendarManager--><!--Device-calendarManager-export interface CalendarManager-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## createCalendar

```TypeScript
createCalendar(calendarAccount: CalendarAccount): Promise<Calendar>
```

根据日历账户信息，创建一个Calendar对象，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR

<!--Device-CalendarManager-createCalendar(calendarAccount: CalendarAccount): Promise<Calendar>--><!--Device-CalendarManager-createCalendar(calendarAccount: CalendarAccount): Promise<Calendar>-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | 是 | 日历账户信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Calendar> | Promise对象，返回创建的Calendar对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因:<br>1. 必填参数为空；<br>2. 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
  // 检查权限是否已成功申请或者参数是否正确。
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
});

```

## createCalendar

```TypeScript
createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void
```

根据日历账户信息，创建一个Calendar对象，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR

<!--Device-CalendarManager-createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void--><!--Device-CalendarManager-createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | 是 | 日历账户信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Calendar> | 是 | 回调函数，当创建账户成功时，err为undefined，data为创建成功的Calendar；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因:<br>1. 必填参数为空；<br>2. 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
  // 检查权限是否已成功申请或者参数是否正确。
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteCalendar

```TypeScript
deleteCalendar(calendar: Calendar): Promise<void>
```

删除指定Calendar对象，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR

<!--Device-CalendarManager-deleteCalendar(calendar: Calendar): Promise<void>--><!--Device-CalendarManager-deleteCalendar(calendar: Calendar): Promise<void>-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| calendar | [Calendar](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-calendar-c.md) | 是 | 即将删除的Calendar对象。无法删除默认账户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因:<br>1. 必填参数为空；<br>2. 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
      // 检查参数是否正确。
      console.error(`Failed to delete calendar. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    // 检查权限是否已成功申请或者参数是否正确。
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((error: BusinessError) => {
  // 检查权限是否已成功申请或者参数是否正确。
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
})

```

## deleteCalendar

```TypeScript
deleteCalendar(calendar: Calendar, callback: AsyncCallback<void>): void
```

删除指定Calendar对象，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CALENDAR or ohos.permission.WRITE_WHOLE_CALENDAR

<!--Device-CalendarManager-deleteCalendar(calendar: Calendar, callback: AsyncCallback<void>): void--><!--Device-CalendarManager-deleteCalendar(calendar: Calendar, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| calendar | [Calendar](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-calendar-c.md) | 是 | 即将删除的Calendar对象。无法删除默认账户。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当删除账户成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因:<br>1. 必填参数为空；<br>2. 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
          // 检查参数是否正确。
          console.error(`Failed to delete calendar. Code: ${err1.code}, message: ${err1.message}`);
        } else {
          console.info('Succeeded in deleting calendar');
        }
      });
    }
  });
}).catch((error: BusinessError) => {
  // 检查权限是否已成功申请或者参数是否正确。
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
})

```

## editEvent

```TypeScript
editEvent(event: Event): Promise<number>
```

通过跳转到日程创建页面创建单个日程，入参Event不填日程id，不支持设置instanceStartTime、instanceEndTime、identifier、attendee、service、isLunar和timeZone属性，也不支持添加重要日程。使用Promise异步回调。使用该接口创建的日程，系统日历可以进行查询和修改，申请到READ_WHOLE_CALENDAR权限的三方应用可以查询，申请到WRITE_WHOLE_CALENDAR权限的三方应用可以修改。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarManager-editEvent(event: Event): Promise<number>--><!--Device-CalendarManager-editEvent(event: Event): Promise<number>-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Event](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact-event-c.md) | 是 | Event对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回日程的id，日程id是日程的唯一标识符，是数据库的自增主键。创建失败时没有返回值；当返回值小于0时代表用户取消创建；当返回值大于0时代表日程创建成功；没有等于0的情况。 |

**示例：**

```TypeScript
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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

获取当前应用所有创建的Calendar对象以及默认Calendar对象，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR

<!--Device-CalendarManager-getAllCalendars(): Promise<Calendar[]>--><!--Device-CalendarManager-getAllCalendars(): Promise<Calendar[]>-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Calendar[]> | Promise对象，返回查询到的Calendar对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因: 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getAllCalendars().then((data: calendarManager.Calendar[]) => {
  console.info(`Succeeded in getting all calendars, data -> ${JSON.stringify(data)}`);
  data.forEach((calendar) => {
    const account = calendar.getAccount();
    console.info(`account -> ${JSON.stringify(account)}`);
  })
}).catch((err: BusinessError) => {
  // 检查权限是否已成功申请。
  console.error(`Failed to get all calendars. Code: ${err.code}, message: ${err.message}`);
  
});

```

## getAllCalendars

```TypeScript
getAllCalendars(callback: AsyncCallback<Calendar[]>): void
```

获取当前应用所有创建的Calendar对象以及默认Calendar对象，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR

<!--Device-CalendarManager-getAllCalendars(callback: AsyncCallback<Calendar[]>): void--><!--Device-CalendarManager-getAllCalendars(callback: AsyncCallback<Calendar[]>): void-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Calendar[]> | 是 | 回调函数，当查询账户成功时，err为undefined，data为查询到的Calendar数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因:<br>1. 必填参数为空；<br>2. 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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

## getCalendar

```TypeScript
getCalendar(calendarAccount?: CalendarAccount): Promise<Calendar>
```

获取默认Calendar对象或者指定Calendar对象，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarManager-getCalendar(calendarAccount?: CalendarAccount): Promise<Calendar>--><!--Device-CalendarManager-getCalendar(calendarAccount?: CalendarAccount): Promise<Calendar>-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | 否 | 指定日历账户信息，用来获取指定Calendar对象，不填时，表示获取默认Calendar对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Calendar> | Promise对象，返回查询到的Calendar对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因: 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900003](../errorcode-calendarManager.md#23900003-未找到指定的账户) | 未找到指定的账户。<br>**适用版本：** 23+ |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getCalendar().then((data: calendarManager.Calendar) => {
  console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  // 检查权限是否已成功申请。
  console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
});

```

## getCalendar

```TypeScript
getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void
```

获取指定Calendar对象，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarManager-getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void--><!--Device-CalendarManager-getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback<Calendar>): void-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| calendarAccount | [CalendarAccount](arkts-calendar-calendarmanager-calendaraccount-i.md) | 是 | 指定日历账户信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Calendar> | 是 | 回调函数，当查询账户成功时，err为undefined，data为查询到的Calendar；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因: 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900003](../errorcode-calendarManager.md#23900003-未找到指定的账户) | 未找到指定的账户。<br>**适用版本：** 23+ |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
      // 检查权限是否已成功申请或者参数是否正确。
    } else {
      console.info(`Succeeded in getting calendar data -> ${JSON.stringify(data)}`);
    }
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to create calendar. Code: ${error.code}, message: ${error.message}`);
  // 检查权限是否已成功申请或者参数是否正确。
})

```

## getCalendar

```TypeScript
getCalendar(callback: AsyncCallback<Calendar>): void
```

获取默认Calendar对象，默认Calendar是日历存储首次运行时创建的，若创建Event时不关注其Calendar归属，则无须通过createCalendar()创建Calendar，直接使用默认Calendar，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CALENDAR or ohos.permission.READ_WHOLE_CALENDAR

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarManager-getCalendar(callback: AsyncCallback<Calendar>): void--><!--Device-CalendarManager-getCalendar(callback: AsyncCallback<Calendar>): void-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Calendar> | 是 | 回调函数，当查询账户成功时，err为undefined，data为查询到的Calendar；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 权限校验失败。 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 参数检查失败，可能原因:<br>1. 必填参数为空；<br>2. 参数类型不正确。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该设备不支持此API。 |
| [23900004](../errorcode-calendarManager.md#23900004-内部程序错误) | 内部程序错误，可能原因:<br>1. dataShare数据库执行错误；<br>2. 空指针错误；<br>3. 数据解析错误。<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
import { calendarMgr } from '../entryability/EntryAbility';
import { calendarManager } from '@kit.CalendarKit';

calendarMgr?.getCalendar((err: BusinessError, data:calendarManager.Calendar) => {
  if (err) {
    // 检查权限是否已成功申请或者参数是否正确。
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
  }
});

```

