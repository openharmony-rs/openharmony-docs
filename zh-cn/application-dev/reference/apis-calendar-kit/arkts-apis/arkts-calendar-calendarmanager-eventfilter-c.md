# EventFilter

日程过滤器，查询日程时进行筛选过滤，获取符合条件的日程。

**起始版本：** 10

<!--Device-calendarManager-class EventFilter--><!--Device-calendarManager-class EventFilter-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

<a id="filterbyid"></a>
## filterById

```TypeScript
static filterById(ids: number[]): EventFilter
```

根据日程id过滤日程。

**起始版本：** 10

<!--Device-EventFilter-static filterById(ids: number[]): EventFilter--><!--Device-EventFilter-static filterById(ids: number[]): EventFilter-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ids | number[] | 是 | 日程id数组，日程id需为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | 返回日程过滤器对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
    // 检查权限是否已成功申请。
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event1).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      id1 = data;
    }).catch((err: BusinessError) => {
      // 检查权限是否已成功申请或者参数是否正确。
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    await calendar.addEvent(event2).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
      id2 = data;
    }).catch((err: BusinessError) => {
      // 检查参数是否正确。
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    const filter = calendarManager.EventFilter.filterById([id1, id2]);
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events filter by id, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // 检查参数是否正确。
      console.error(`Failed to filter by id. Code: ${err.code}, message: ${err.message}`);
    });
  }
});

```

<a id="filterbytime"></a>
## filterByTime

```TypeScript
static filterByTime(start: number, end: number): EventFilter
```

根据日程时间过滤日程。

**起始版本：** 10

<!--Device-EventFilter-static filterByTime(start: number, end: number): EventFilter--><!--Device-EventFilter-static filterByTime(start: number, end: number): EventFilter-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 开始时间。格式为13位时间戳。 |
| end | number | 是 | 结束时间。格式为13位时间戳。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | 返回日程过滤器对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
    // 检查权限是否已成功申请。
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event1).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // 检查权限是否已成功申请或者参数是否正确。
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    await calendar.addEvent(event2).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
      // 检查参数是否正确。
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    const filter = calendarManager.EventFilter.filterByTime(1686931200000, 1687017600000);
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events filter by time, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // 检查参数是否正确。
      console.error(`Failed to filter by time. Code: ${err.code}, message: ${err.message}`);
    });
  }
});

```

<a id="filterbytitle"></a>
## filterByTitle

```TypeScript
static filterByTitle(title: string): EventFilter
```

根据日程标题过滤日程，该条件为模糊匹配。

**起始版本：** 10

<!--Device-EventFilter-static filterByTitle(title: string): EventFilter--><!--Device-EventFilter-static filterByTitle(title: string): EventFilter-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| title | string | 是 | 日程标题。长度建议为[0,5000]字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EventFilter](arkts-calendar-calendarmanager-eventfilter-c.md) | 返回日程过滤器对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// EntryAbility文件须按照calendarManager.getCalendarManager处示例代码进行配置
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
    // 检查权限是否已成功申请。
    console.error(`Failed to get calendar. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting calendar, data -> ${JSON.stringify(data)}`);
    calendar = data;
    await calendar.addEvent(event).then((data: number) => {
      console.info(`Succeeded in adding event, id -> ${data}`);
    }).catch((err: BusinessError) => {
       // 检查权限是否已成功申请或者参数是否正确。
      console.error(`Failed to add event. Code: ${err.code}, message: ${err.message}`);
    });
    const filter = calendarManager.EventFilter.filterByTitle('MyEvent');
    calendar.getEvents(filter).then((data: calendarManager.Event[]) => {
      console.info(`Succeeded in getting events filter by title, data -> ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      // 检查参数是否正确。
      console.error(`Failed to filter by title. Code: ${err.code}, message: ${err.message}`);
    });
  }
});

```

