# ReminderRequest

提醒实例对象，用于设置提醒类型、响铃时长等具体信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md)

<!--Device-reminderAgent-interface ReminderRequest--><!--Device-reminderAgent-interface ReminderRequest-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## actionButton

```TypeScript
actionButton?: [ActionButton?, ActionButton?]
```

弹出的提醒通知栏中显示的按钮（参数可选，支持0/1/2个按钮）。

**类型：** [ActionButton?, ActionButton?]

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [actionButton](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#actionbutton)

<!--Device-ReminderRequest-actionButton?: [ActionButton?, ActionButton?]--><!--Device-ReminderRequest-actionButton?: [ActionButton?, ActionButton?]-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## content

```TypeScript
content?: string
```

指明提醒内容。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [content](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#content)

<!--Device-ReminderRequest-content?: string--><!--Device-ReminderRequest-content?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## expiredContent

```TypeScript
expiredContent?: string
```

指明提醒过期后需要显示的内容。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [expiredContent](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#expiredcontent)

<!--Device-ReminderRequest-expiredContent?: string--><!--Device-ReminderRequest-expiredContent?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## maxScreenWantAgent

```TypeScript
maxScreenWantAgent?: MaxScreenWantAgent
```

提醒到达时跳转的目标包。如果设备正在使用中，则弹出一个通知框。

**类型：** MaxScreenWantAgent

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxScreenWantAgent](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#maxscreenwantagent)

<!--Device-ReminderRequest-maxScreenWantAgent?: MaxScreenWantAgent--><!--Device-ReminderRequest-maxScreenWantAgent?: MaxScreenWantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## notificationId

```TypeScript
notificationId?: number
```

指明提醒使用的通知的id号，相同id号的提醒会覆盖。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [notificationId](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#notificationid)

<!--Device-ReminderRequest-notificationId?: number--><!--Device-ReminderRequest-notificationId?: number-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## reminderType

```TypeScript
reminderType: ReminderType
```

指明提醒类型。

**类型：** ReminderType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reminderType](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#remindertype)

<!--Device-ReminderRequest-reminderType: ReminderType--><!--Device-ReminderRequest-reminderType: ReminderType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## ringDuration

```TypeScript
ringDuration?: number
```

指明响铃时长（单位：秒），默认1秒。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ringDuration](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#ringduration)

<!--Device-ReminderRequest-ringDuration?: number--><!--Device-ReminderRequest-ringDuration?: number-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## slotType

```TypeScript
slotType?: notification.SlotType
```

指明提醒的slot类型。

**类型：** notification.SlotType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [slotType](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#slottype)

<!--Device-ReminderRequest-slotType?: notification.SlotType--><!--Device-ReminderRequest-slotType?: notification.SlotType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeContent

```TypeScript
snoozeContent?: string
```

指明延迟提醒时需要显示的内容。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [snoozeContent](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#snoozecontent)

<!--Device-ReminderRequest-snoozeContent?: string--><!--Device-ReminderRequest-snoozeContent?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## snoozeTimes

```TypeScript
snoozeTimes?: number
```

指明延迟提醒次数，默认0次。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [snoozeTimes](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#snoozetimes)

<!--Device-ReminderRequest-snoozeTimes?: number--><!--Device-ReminderRequest-snoozeTimes?: number-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## timeInterval

```TypeScript
timeInterval?: number
```

执行延迟提醒间隔（单位：秒），默认0秒。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [timeInterval](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#timeinterval)

<!--Device-ReminderRequest-timeInterval?: number--><!--Device-ReminderRequest-timeInterval?: number-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## title

```TypeScript
title?: string
```

指明提醒标题。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [title](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#title)

<!--Device-ReminderRequest-title?: string--><!--Device-ReminderRequest-title?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

点击通知后需要跳转的目标ability信息。

**类型：** WantAgent

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [wantAgent](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#wantagent)

<!--Device-ReminderRequest-wantAgent?: WantAgent--><!--Device-ReminderRequest-wantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

