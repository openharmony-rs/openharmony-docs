# ReminderRequest

Defines the request for publishing a reminder.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## forceDistributed

```TypeScript
forceDistributed?: boolean
```

Whether notifications are forcibly displayed in all scenarios across devices. The default value is **false**. For details, see [NotificationRequest.forceDistributed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i-sys.md#forcedistributed)  
- **true**: Notifications are displayed on all collaboration devices.  
- **false**: Notifications are displayed on the applications that are on the collaborative management list.

**Type:** boolean

**Default:** false

**Since:** 23

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.

## notDistributed

```TypeScript
notDistributed?: boolean
```

Whether notifications are not displayed in all scenarios across devices. The default value is **false**. For details, see [NotificationRequest.notDistributed](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i-sys.md#notdistributed)  
- **true**: Notifications are displayed only on the local device.  
- **false**: Notifications are displayed on all collaborative devices.

**Type:** boolean

**Default:** false

**Since:** 23

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.
