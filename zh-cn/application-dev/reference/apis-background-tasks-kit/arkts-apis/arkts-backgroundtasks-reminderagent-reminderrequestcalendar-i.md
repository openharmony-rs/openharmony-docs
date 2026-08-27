# ReminderRequestCalendar

日历实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestCalendar extends [ReminderRequest](arkts-backgroundtasks-reminderagent-reminderrequest-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ReminderRequestCalendar](arkts-backgroundtasks-reminderagentmanager-reminderrequestcalendar-i.md)

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## dateTime

```TypeScript
dateTime: LocalDateTime
```

指明提醒的目标时间。

**类型：** LocalDateTime

**起始版本：** 7

**废弃版本：** 9

**替代接口：** dateTime

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatDays

```TypeScript
repeatDays?: Array<number>
```

指明重复提醒的日期。

**类型：** Array&lt;number&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** repeatDays

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatMonths

```TypeScript
repeatMonths?: Array<number>
```

指明重复提醒的月份。

**类型：** Array&lt;number&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** repeatMonths

**系统能力：** SystemCapability.Notification.ReminderAgent
