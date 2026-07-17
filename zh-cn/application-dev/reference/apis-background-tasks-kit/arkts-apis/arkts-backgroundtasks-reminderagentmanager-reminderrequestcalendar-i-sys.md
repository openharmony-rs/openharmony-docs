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

## rruleWantAgent

```TypeScript
rruleWantAgent?: WantAgent
```

自定义重复日程，指明需要拉起的 Service Extension。

**类型：** WantAgent

**起始版本：** 12

<!--Device-ReminderRequestCalendar-rruleWantAgent?: WantAgent--><!--Device-ReminderRequestCalendar-rruleWantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**系统接口：** 此接口为系统接口。

