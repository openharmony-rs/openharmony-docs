# ReminderRequestTimer

ReminderRequestTimer extends ReminderRequest

倒计时实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestTimer extends [ReminderRequest](arkts-backgroundtasks-reminderrequest-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatCount

```TypeScript
repeatCount?: number
```

重复次数，默认值为0，无限次重复。需和repeatInterval一起使用。

范围：[0, +∞)。超出范围返回错误码401。

26.0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.ReminderAgent

## repeatInterval

```TypeScript
repeatInterval?: number
```

重复周期，无默认值，未赋值时，无重复周期。需和repeatCount一起使用。

单位：s，范围：[86400, +∞)。超出范围返回错误码401。

26.0.0

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.ReminderAgent

## triggerTimeInSeconds

```TypeScript
triggerTimeInSeconds: number
```

指明倒计时的秒数。

单位：s

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

