# ReminderRequestAlarm

ReminderRequestAlarm extends ReminderRequest

闹钟实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestAlarm extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**起始版本：** 9

<!--Device-reminderAgentManager-interface ReminderRequestAlarm extends ReminderRequest--><!--Device-reminderAgentManager-interface ReminderRequestAlarm extends ReminderRequest-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## daysOfWeek

```TypeScript
daysOfWeek?: Array<number>
```

指明每周哪几天需要重复提醒。范围为周一到周日，对应数字为1到7，默认为空。

**类型：** Array<number>

**起始版本：** 9

<!--Device-ReminderRequestAlarm-daysOfWeek?: Array<int>--><!--Device-ReminderRequestAlarm-daysOfWeek?: Array<int>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: number
```

指明提醒的目标时刻，范围：[0, 23]。

**类型：** number

**起始版本：** 9

<!--Device-ReminderRequestAlarm-hour: int--><!--Device-ReminderRequestAlarm-hour: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: number
```

指明提醒的目标分钟，范围：[0, 59]。

**类型：** number

**起始版本：** 9

<!--Device-ReminderRequestAlarm-minute: int--><!--Device-ReminderRequestAlarm-minute: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

