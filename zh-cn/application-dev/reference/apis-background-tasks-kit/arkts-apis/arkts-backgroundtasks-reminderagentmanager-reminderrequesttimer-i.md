# ReminderRequestTimer

ReminderRequestTimer extends ReminderRequest 倒计时实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestTimer extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

**起始版本：** 23

<!--Device-reminderAgentManager-interface ReminderRequestTimer--><!--Device-reminderAgentManager-interface ReminderRequestTimer-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## repeatCount

```TypeScript
repeatCount?: int
```

重复次数，默认值为0，无限次重复。需和repeatInterval一起使用。 范围：[0, +∞)。超出范围返回错误码401。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderRequestTimer-repeatCount?: int--><!--Device-ReminderRequestTimer-repeatCount?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatInterval

```TypeScript
repeatInterval?: long
```

重复周期，无默认值，未赋值时，无重复周期。需和repeatCount一起使用。 单位：s，范围：[86400, +∞)。超出范围返回错误码401。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderRequestTimer-repeatInterval?: long--><!--Device-ReminderRequestTimer-repeatInterval?: long-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## triggerTimeInSeconds

```TypeScript
triggerTimeInSeconds: long
```

指明倒计时的秒数。 单位：s

**类型：** long

**起始版本：** 23

<!--Device-ReminderRequestTimer-triggerTimeInSeconds: long--><!--Device-ReminderRequestTimer-triggerTimeInSeconds: long-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

