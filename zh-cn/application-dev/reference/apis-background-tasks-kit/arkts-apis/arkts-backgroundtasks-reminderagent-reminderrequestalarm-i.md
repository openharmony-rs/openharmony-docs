# ReminderRequestAlarm

闹钟实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestAlarm extends [ReminderRequest](arkts-backgroundtasks-reminderagent-reminderrequest-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ReminderRequestAlarm](arkts-backgroundtasks-reminderagentmanager-reminderrequestalarm-i.md)

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## daysOfWeek

```TypeScript
daysOfWeek?: Array<number>
```

指明每周哪几天需要重复提醒。范围为周一到周末，对应数字为1到7。

**类型：** Array&lt;number&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** daysOfWeek

**系统能力：** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: number
```

指明提醒的目标时刻。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hour

**系统能力：** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: number
```

指明提醒的目标分钟。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** minute

**系统能力：** SystemCapability.Notification.ReminderAgent
