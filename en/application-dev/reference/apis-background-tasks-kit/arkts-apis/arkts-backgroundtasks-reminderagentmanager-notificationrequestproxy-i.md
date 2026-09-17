# NotificationRequestProxy

Notification request proxy.

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## appMessageId

```TypeScript
appMessageId?: string
```

Unique ID carried in a notification sent by an application, which is used for notification deduplication. This parameter is left empty by default. For details, see [NotificationRequest.appMessageId](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md).

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## isAlertOnce

```TypeScript
isAlertOnce?: boolean
```

Whether to send a notification alert only once when a notification is published or updated. The default value is **false**. For details, see [NotificationRequest.isAlertOnce](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md).

- **true**: An alert is sent only when the notification is published for the first time. For subsequent update,  
the alert mode is changed to [LEVEL_LOW](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-slotlevel-e.md).  
- **false**: The alert is sent in the configured alert mode.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent
