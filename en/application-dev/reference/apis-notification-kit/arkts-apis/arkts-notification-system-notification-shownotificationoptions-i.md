# ShowNotificationOptions

```TypeScript
export interface ShowNotificationOptions
```

Options for displaying the notification, including the notification title, notification content, and the action triggered when the notification is tapped.

**Since:** 3

**Deprecated since:** 7

<!--Device-unnamed-export interface ShowNotificationOptions--><!--Device-unnamed-export interface ShowNotificationOptions-End-->

**System capability:** SystemCapability.Notification.Notification

## Modules to Import

```TypeScript
import { Notification, ActionResult, ShowNotificationOptions } from '@kit.NotificationKit';
```

## clickAction

```TypeScript
clickAction?: ActionResult
```

Action triggered when the notification is tapped.

**Type:** [ActionResult](arkts-notification-system-notification-actionresult-i.md)

**Since:** 3

**Deprecated since:** 7

<!--Device-ShowNotificationOptions-clickAction?: ActionResult--><!--Device-ShowNotificationOptions-clickAction?: ActionResult-End-->

**System capability:** SystemCapability.Notification.Notification

## contentText

```TypeScript
contentText?: string
```

[Notification content](../../../notification/notification-glossary.md#notification-content).

**Type:** string

**Since:** 3

**Deprecated since:** 7

<!--Device-ShowNotificationOptions-contentText?: string--><!--Device-ShowNotificationOptions-contentText?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## contentTitle

```TypeScript
contentTitle?: string
```

Notification title.

**Type:** string

**Since:** 3

**Deprecated since:** 7

<!--Device-ShowNotificationOptions-contentTitle?: string--><!--Device-ShowNotificationOptions-contentTitle?: string-End-->

**System capability:** SystemCapability.Notification.Notification
