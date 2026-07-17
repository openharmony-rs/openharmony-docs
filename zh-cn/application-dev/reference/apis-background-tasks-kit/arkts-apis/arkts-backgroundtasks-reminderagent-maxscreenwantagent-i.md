# MaxScreenWantAgent

全屏显示提醒到达时自动拉起的目标ability信息，该接口预留。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [MaxScreenWantAgent](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md)

<!--Device-reminderAgent-interface MaxScreenWantAgent--><!--Device-reminderAgent-interface MaxScreenWantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgent } from '@kit.BackgroundTasksKit';
```

## abilityName

```TypeScript
abilityName: string
```

指明提醒到达时自动拉起的目标ability名（如果设备在使用中，则只弹出通知横幅框）。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [abilityName](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md#abilityname)

<!--Device-MaxScreenWantAgent-abilityName: string--><!--Device-MaxScreenWantAgent-abilityName: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## pkgName

```TypeScript
pkgName: string
```

指明提醒到达时自动拉起的目标HAP名（如果设备在使用中，则只弹出通知横幅框）。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [pkgName](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md#pkgname)

<!--Device-MaxScreenWantAgent-pkgName: string--><!--Device-MaxScreenWantAgent-pkgName: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

