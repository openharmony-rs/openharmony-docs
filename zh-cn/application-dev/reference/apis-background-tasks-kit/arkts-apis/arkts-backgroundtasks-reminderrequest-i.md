# ReminderRequest

代理提醒对象，用于设置提醒类型、响铃时长等具体信息。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## actionButton

```TypeScript
actionButton?: [ActionButton?, ActionButton?, ActionButton?]
```

弹出的提醒通知中显示的按钮。

针对三方应用：最多支持两个按钮。

针对系统应用：从API version 10开始最多支持三个按钮，API version 10之前的版本最多支持两个按钮。

**类型：** [ActionButton?, ActionButton?, ActionButton?]

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## autoDeletedTime

```TypeScript
autoDeletedTime?: number
```

自动清除的时间。

数据格式：时间戳，单位：ms，具体请参考
[NotificationRequest.autoDeletedTime](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-i.md#autodeletedtime)

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Notification.ReminderAgent

## content

```TypeScript
content?: string
```

指明提醒内容。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## contentResourceId

```TypeScript
contentResourceId?: number
```

指明提醒内容的资源ID，通过`$r(资源名称).id`方法获取。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Notification.ReminderAgent

## customRingUri

```TypeScript
customRingUri?: string
```

指明自定义提示音的uri，提示音文件必须放在resources/rawfile目录下，支持m4a、aac、mp3、ogg、wav、flac、amr等格式。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Notification.ReminderAgent

## expiredContent

```TypeScript
expiredContent?: string
```

指明提醒过期后需要显示的内容。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## expiredContentResourceId

```TypeScript
expiredContentResourceId?: number
```

指明提醒过期后内容的资源ID，通过`$r(资源名称).id`方法获取。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Notification.ReminderAgent

## groupId

```TypeScript
groupId?: string
```

指明提醒使用相同的组id。相同组id中，一个提醒被点击不在提醒后，组内其他提醒也会被取消。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Notification.ReminderAgent

## maxScreenWantAgent

```TypeScript
maxScreenWantAgent?: MaxScreenWantAgent
```

提醒到达时，全屏显示自动拉起目标的ability信息。如果设备正在使用中，则弹出一个通知横幅框。

说明：该接口为预留接口，暂不支持使用。

**类型：** MaxScreenWantAgent

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## notificationId

```TypeScript
notificationId?: number
```

指明提醒使用的通知的id号，需开发者传入，相同id号的提醒会覆盖，默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## reminderType

```TypeScript
reminderType: ReminderType
```

指明代理提醒类型。

**类型：** ReminderType

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## ringChannel

```TypeScript
ringChannel?: RingChannel
```

指明自定义提示音的音频播放通道，默认为闹钟通道。

**类型：** RingChannel

**起始版本：** 20

**系统能力：** SystemCapability.Notification.ReminderAgent

## ringDuration

```TypeScript
ringDuration?: number
```

指明响铃时长。

单位：s，默认1s，范围：[0, 1800]。

值为0时：跟随系统设置中的通知铃声。

值大于0时：如果设置了[ReminderRequest.customRingUri](arkts-backgroundtasks-reminderrequest-i.md)，则在指定的通道
[ReminderRequest.ringChannel](arkts-backgroundtasks-reminderrequest-i.md)上响铃。否则使用代理提醒默认的自定义提示音。

响铃同时会触发振动，从API版本26.0.0开始，支持长振动，振动时长与响铃时长一致。API版本26.0.0之前版本，响铃时会快速振动一次。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## slotType

```TypeScript
slotType?: notification.SlotType
```

指明提醒的通道渠道类型。

**类型：** notification.SlotType

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeContent

```TypeScript
snoozeContent?: string
```

指明延时提醒时需要显示的内容（不适用于倒计时提醒类型）。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeContentResourceId

```TypeScript
snoozeContentResourceId?: number
```

指明延时提醒内容的资源ID，通过`$r(资源名称).id`方法获取。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeSlotType

```TypeScript
snoozeSlotType?: notification.SlotType
```

指明延时提醒的通道渠道类型（不适用于倒计时提醒类型）。

**类型：** notification.SlotType

**起始版本：** 11

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeTimes

```TypeScript
snoozeTimes?: number
```

指明延时提醒次数，默认0次（不适用于倒计时提醒类型）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## tapDismissed

```TypeScript
tapDismissed?: boolean
```

通知是否自动清除，默认值为true，具体请参考
[NotificationRequest.tapDismissed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-i.md#tapdismissed)

- true：点击通知消息或通知按钮后，自动删除当前通知。
- false：点击通知消息或通知按钮后，保留当前通知。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Notification.ReminderAgent

## timeInterval

```TypeScript
timeInterval?: number
```

执行延时提醒间隔。

单位：s，最少30s（不适用于倒计时提醒类型）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## title

```TypeScript
title?: string
```

指明提醒标题。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## titleResourceId

```TypeScript
titleResourceId?: number
```

指明提醒标题的资源ID，通过`$r(资源名称).id`方法获取。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Notification.ReminderAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

点击通知后需要跳转的目标ability信息。

**类型：** WantAgent

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

