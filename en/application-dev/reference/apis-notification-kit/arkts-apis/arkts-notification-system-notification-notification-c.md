# Notification

```TypeScript
declare class Notification
```

Manages notifications.

**Since:** 3

**Deprecated since:** 7

**Substitutes:** [notification/notification](arkts-notification-notification.md)

<!--Device-unnamed-declare class Notification--><!--Device-unnamed-declare class Notification-End-->

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { Notification, ActionResult, ShowNotificationOptions } from '@kit.NotificationKit';
```

## show

```TypeScript
static show(options?: ShowNotificationOptions): void
```

Displays a notification.

**Since:** 3

**Deprecated since:** 7

**Substitutes:** [notification/notification](arkts-notification-notification.md)

<!--Device-Notification-static show(options?: ShowNotificationOptions): void--><!--Device-Notification-static show(options?: ShowNotificationOptions): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShowNotificationOptions](arkts-notification-system-notification-shownotificationoptions-i.md) | No | Options for displaying the notification, including the notification title, notification content, and the action triggered when the notification is tapped. |

**Examples**

```TypeScript
let notificationObj: notification = {
  show() {
    notification.show({
      contentTitle: 'title info',
      contentText: 'text',
      clickAction: {
        bundleName: 'com.example.testapp',
        abilityName: 'notificationDemo',
        uri: '/path/to/notification'
      }
    });
  }
}
```
