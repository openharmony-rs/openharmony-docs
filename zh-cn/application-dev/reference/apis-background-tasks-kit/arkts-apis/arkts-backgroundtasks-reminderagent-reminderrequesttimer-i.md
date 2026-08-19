# ReminderRequestTimer

倒计时实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestTimer extends [ReminderRequest](arkts-backgroundtasks-reminderagent-reminderrequest-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ReminderRequestTimer](arkts-backgroundtasks-reminderagentmanager-reminderrequesttimer-i.md)

<!--Device-reminderAgent-interface ReminderRequestTimer--><!--Device-reminderAgent-interface ReminderRequestTimer-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## triggerTimeInSeconds

```TypeScript
triggerTimeInSeconds: number
```

指明倒计时的秒数。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** triggerTimeInSeconds

<!--Device-ReminderRequestTimer-triggerTimeInSeconds: number--><!--Device-ReminderRequestTimer-triggerTimeInSeconds: number-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

