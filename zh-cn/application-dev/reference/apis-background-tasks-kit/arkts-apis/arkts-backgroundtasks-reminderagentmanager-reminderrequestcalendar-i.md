# ReminderRequestCalendar

ReminderRequestCalendar extends ReminderRequest

日历实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestCalendar extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**起始版本：** 9

<!--Device-reminderAgentManager-interface ReminderRequestCalendar extends ReminderRequest--><!--Device-reminderAgentManager-interface ReminderRequestCalendar extends ReminderRequest-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## dateTime

```TypeScript
dateTime: LocalDateTime
```

指明提醒的目标时间。

**类型：** LocalDateTime

**起始版本：** 9

<!--Device-ReminderRequestCalendar-dateTime: LocalDateTime--><!--Device-ReminderRequestCalendar-dateTime: LocalDateTime-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## daysOfWeek

```TypeScript
daysOfWeek?: Array<number>
```

指明每周哪几天需要重复提醒。范围为周一到周日，对应数字为1到7，默认为空。

**类型：** Array<number>

**起始版本：** 11

<!--Device-ReminderRequestCalendar-daysOfWeek?: Array<int>--><!--Device-ReminderRequestCalendar-daysOfWeek?: Array<int>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## endDateTime

```TypeScript
endDateTime?: LocalDateTime
```

指明提醒的结束时间。

**类型：** LocalDateTime

**起始版本：** 12

<!--Device-ReminderRequestCalendar-endDateTime?: LocalDateTime--><!--Device-ReminderRequestCalendar-endDateTime?: LocalDateTime-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatDays

```TypeScript
repeatDays?: Array<number>
```

指明重复提醒的日期，范围：[1, 31]，默认为空。需和repeatMonths一起使用。

**类型：** Array<number>

**起始版本：** 9

<!--Device-ReminderRequestCalendar-repeatDays?: Array<int>--><!--Device-ReminderRequestCalendar-repeatDays?: Array<int>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatMonths

```TypeScript
repeatMonths?: Array<number>
```

指明重复提醒的月份，范围：[1, 12]，默认为空。需和repeatDays一起使用。

**类型：** Array<number>

**起始版本：** 9

<!--Device-ReminderRequestCalendar-repeatMonths?: Array<int>--><!--Device-ReminderRequestCalendar-repeatMonths?: Array<int>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

