# NotificationReminderInfo（系统接口）

描述指定应用提醒方式信息。

**起始版本：** 21

<!--Device-notificationManager-export interface NotificationReminderInfo--><!--Device-notificationManager-export interface NotificationReminderInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundle

```TypeScript
bundle: BundleOption
```

指定应用的包信息。

**类型：** BundleOption

**起始版本：** 21

<!--Device-NotificationReminderInfo-bundle: BundleOption--><!--Device-NotificationReminderInfo-bundle: BundleOption-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## reminderFlags

```TypeScript
reminderFlags: number
```

表示通知提醒方式的标志位。

**类型：** number

**起始版本：** 21

<!--Device-NotificationReminderInfo-reminderFlags: long--><!--Device-NotificationReminderInfo-reminderFlags: long-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## silentReminderEnabled

```TypeScript
silentReminderEnabled: boolean
```

表示静默提醒开关使能状态（true：使能，false：禁止）。

**类型：** boolean

**起始版本：** 21

<!--Device-NotificationReminderInfo-silentReminderEnabled: boolean--><!--Device-NotificationReminderInfo-silentReminderEnabled: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

