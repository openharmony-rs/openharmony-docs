# NotificationReminderInfo（系统接口）

```TypeScript
export interface NotificationReminderInfo
```

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

**类型：** [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)

**起始版本：** 21

<!--Device-NotificationReminderInfo-bundle: BundleOption--><!--Device-NotificationReminderInfo-bundle: BundleOption-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## reminderFlags

```TypeScript
reminderFlags: number
```

表示[通知提醒方式](../../../notification/notification-glossary.md#notification-reminder-mode通知提醒方式)的标志位。

- bit0：铃声提示。0表示关闭，1表示开启。  
- bit1：锁屏。0表示关闭，1表示开启。  
- bit2：横幅。0表示关闭，1表示开启。  
- bit3：亮屏。0表示关闭，1表示开启。  
- bit4：振动。0表示关闭，1表示开启。  
- bit5：状态栏通知图标。0表示关闭，1表示开启。

**类型：** number

**起始版本：** 21

<!--Device-NotificationReminderInfo-reminderFlags: long--><!--Device-NotificationReminderInfo-reminderFlags: long-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## silentReminderEnabled

```TypeScript
silentReminderEnabled: boolean
```

表示[静默提醒](../../../notification/notification-glossary.md#silent-reminder静默提醒)开关使能状态（true：使能，false：禁止）。

**类型：** boolean

**起始版本：** 21

<!--Device-NotificationReminderInfo-silentReminderEnabled: boolean--><!--Device-NotificationReminderInfo-silentReminderEnabled: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
