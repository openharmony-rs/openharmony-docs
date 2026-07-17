# ReminderRequest

代理提醒对象，用于设置提醒类型、响铃时长等具体信息。

**起始版本：** 9

<!--Device-reminderAgentManager-interface ReminderRequest--><!--Device-reminderAgentManager-interface ReminderRequest-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## forceDistributed

```TypeScript
forceDistributed?: boolean
```

通知是否强制进行全场景跨设备协同显示，默认为false。具体请参考[NotificationRequest.forceDistributed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i-sys.md#forcedistributed)

- 设置为true时：通知将在所有协同设备上显示。  
- 设置为false时：通知将按照协同管控名单显示。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**默认值：** false

**起始版本：** 23

<!--Device-ReminderRequest-forceDistributed?: boolean--><!--Device-ReminderRequest-forceDistributed?: boolean-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**系统接口：** 此接口为系统接口。

## notDistributed

```TypeScript
notDistributed?: boolean
```

通知是否不进行全场景跨设备协同显示，默认为false。具体请参考[NotificationRequest.notDistributed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i-sys.md#notdistributed)

- 设置为true时：通知仅在本设备上显示。  
- 设置为false时：通知将在所有协同设备上显示。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**默认值：** false

**起始版本：** 23

<!--Device-ReminderRequest-notDistributed?: boolean--><!--Device-ReminderRequest-notDistributed?: boolean-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**系统接口：** 此接口为系统接口。

