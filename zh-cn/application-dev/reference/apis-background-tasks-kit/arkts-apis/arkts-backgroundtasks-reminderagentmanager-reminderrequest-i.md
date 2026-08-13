# ReminderRequest

代理提醒对象，用于设置提醒类型、响铃时长等具体信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-reminderAgentManager-interface ReminderRequest--><!--Device-reminderAgentManager-interface ReminderRequest-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## actionButton

```TypeScript
actionButton?: Array<ActionButton>
```

Action button displayed on the reminder notification.

**类型：** Array&lt;ActionButton&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-actionButton?: Array<ActionButton>--><!--Device-ReminderRequest-actionButton?: Array<ActionButton>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## autoDeletedTime

```TypeScript
autoDeletedTime?: long
```

自动清除的时间。 数据格式：时间戳，单位：ms，具体请参考 [NotificationRequest.autoDeletedTime](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md#autoDeletedTime)

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-autoDeletedTime?: long--><!--Device-ReminderRequest-autoDeletedTime?: long-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## content

```TypeScript
content?: string
```

指明提醒内容。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-content?: string--><!--Device-ReminderRequest-content?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## contentResourceId

```TypeScript
contentResourceId?: int
```

指明提醒内容的资源ID，通过`\$r(资源名称).id`方法获取。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-contentResourceId?: int--><!--Device-ReminderRequest-contentResourceId?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## customRingUri

```TypeScript
customRingUri?: string
```

指明自定义提示音的uri，提示音文件必须放在resources/rawfile目录下，支持m4a、aac、mp3、ogg、wav、flac、amr等格式。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-customRingUri?: string--><!--Device-ReminderRequest-customRingUri?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## expiredContent

```TypeScript
expiredContent?: string
```

指明提醒过期后需要显示的内容。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-expiredContent?: string--><!--Device-ReminderRequest-expiredContent?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## expiredContentResourceId

```TypeScript
expiredContentResourceId?: int
```

指明提醒过期后内容的资源ID，通过`\$r(资源名称).id`方法获取。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-expiredContentResourceId?: int--><!--Device-ReminderRequest-expiredContentResourceId?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## fixedTimeZone

```TypeScript
fixedTimeZone?: TimeZoneType
```

时区类型，默认为TimeZoneType.DEFAULT。

**类型：** [TimeZoneType](arkts-backgroundtasks-reminderagentmanager-timezonetype-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderRequest-fixedTimeZone?: TimeZoneType--><!--Device-ReminderRequest-fixedTimeZone?: TimeZoneType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## groupId

```TypeScript
groupId?: string
```

指明提醒使用相同的组id。相同组id中，一个提醒被点击不在提醒后，组内其他提醒也会被取消。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-groupId?: string--><!--Device-ReminderRequest-groupId?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## maxScreenWantAgent

```TypeScript
maxScreenWantAgent?: MaxScreenWantAgent
```

提醒到达时，全屏显示自动拉起目标的ability信息。如果设备正在使用中，则弹出一个通知横幅框。 说明：该接口为预留接口，暂不支持使用。

**类型：** MaxScreenWantAgent

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-maxScreenWantAgent?: MaxScreenWantAgent--><!--Device-ReminderRequest-maxScreenWantAgent?: MaxScreenWantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## notificationId

```TypeScript
notificationId?: int
```

指明提醒使用的通知的id号，需开发者传入，相同id号的提醒会覆盖，默认值为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-notificationId?: int--><!--Device-ReminderRequest-notificationId?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## notificationRequestProxy

```TypeScript
notificationRequestProxy?: NotificationRequestProxy
```

通知请求信息，默认为空。

**类型：** [NotificationRequestProxy](arkts-backgroundtasks-reminderagentmanager-notificationrequestproxy-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderRequest-notificationRequestProxy?: NotificationRequestProxy--><!--Device-ReminderRequest-notificationRequestProxy?: NotificationRequestProxy-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## reminderType

```TypeScript
reminderType: ReminderType
```

指明代理提醒类型。

**类型：** ReminderType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-reminderType: ReminderType--><!--Device-ReminderRequest-reminderType: ReminderType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## ringChannel

```TypeScript
ringChannel?: RingChannel
```

指明自定义提示音的音频播放通道，默认为闹钟通道。

**类型：** [RingChannel](arkts-backgroundtasks-reminderagentmanager-ringchannel-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-ringChannel?: RingChannel--><!--Device-ReminderRequest-ringChannel?: RingChannel-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## ringDuration

```TypeScript
ringDuration?: long
```

指明响铃时长。 单位：s，默认1s，范围：[0, 1800]。 值为0时：跟随系统设置中的通知铃声。 值大于0时：如果设置了[ReminderRequest.customRingUri](#ReminderRequest)，则在指定的通道 [ReminderRequest.ringChannel](#ReminderRequest)上响铃。否则使用代理提醒默认的自定义提示音。 响铃同时会触发振动，从API版本26.0.0开始，支持长振动，振动时长与响铃时长一致。API版本26.0.0之前版本，响铃时会快速振动一次。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-ringDuration?: long--><!--Device-ReminderRequest-ringDuration?: long-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## slotType

```TypeScript
slotType?: notification.SlotType
```

指明提醒的通道渠道类型。

**类型：** notification.SlotType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-slotType?: notification.SlotType--><!--Device-ReminderRequest-slotType?: notification.SlotType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeContent

```TypeScript
snoozeContent?: string
```

指明延时提醒时需要显示的内容（不适用于倒计时提醒类型）。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-snoozeContent?: string--><!--Device-ReminderRequest-snoozeContent?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeContentResourceId

```TypeScript
snoozeContentResourceId?: int
```

指明延时提醒内容的资源ID，通过`\$r(资源名称).id`方法获取。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-snoozeContentResourceId?: int--><!--Device-ReminderRequest-snoozeContentResourceId?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeSlotType

```TypeScript
snoozeSlotType?: notification.SlotType
```

指明延时提醒的通道渠道类型（不适用于倒计时提醒类型）。

**类型：** notification.SlotType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-snoozeSlotType?: notification.SlotType--><!--Device-ReminderRequest-snoozeSlotType?: notification.SlotType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeTimes

```TypeScript
snoozeTimes?: int
```

指明延时提醒次数，默认0次（不适用于倒计时提醒类型）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-snoozeTimes?: int--><!--Device-ReminderRequest-snoozeTimes?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## tapDismissed

```TypeScript
tapDismissed?: boolean
```

通知是否自动清除，默认值为true，具体请参考 [NotificationRequest.tapDismissed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md#tapDismissed) - true：点击通知消息或通知按钮后，自动删除当前通知。 - false：点击通知消息或通知按钮后，保留当前通知。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-tapDismissed?: boolean--><!--Device-ReminderRequest-tapDismissed?: boolean-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## timeInterval

```TypeScript
timeInterval?: long
```

执行延时提醒间隔。 单位：s，最少30s（不适用于倒计时提醒类型）。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-timeInterval?: long--><!--Device-ReminderRequest-timeInterval?: long-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## title

```TypeScript
title?: string
```

指明提醒标题。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-title?: string--><!--Device-ReminderRequest-title?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## titleResourceId

```TypeScript
titleResourceId?: int
```

指明提醒标题的资源ID，通过`\$r(资源名称).id`方法获取。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-titleResourceId?: int--><!--Device-ReminderRequest-titleResourceId?: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

点击通知后需要跳转的目标ability信息。

**类型：** WantAgent

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequest-wantAgent?: WantAgent--><!--Device-ReminderRequest-wantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

