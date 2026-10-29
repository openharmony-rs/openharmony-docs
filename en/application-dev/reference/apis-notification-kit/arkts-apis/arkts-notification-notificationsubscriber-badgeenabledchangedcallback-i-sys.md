# BadgeEnabledChangedCallback (System API)

```TypeScript
export interface BadgeEnabledChangedCallback
```

type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) =&gt; void

Defines a callback function to listen for the enabled state changes of the application badge.

**Since:** 12

<!--Device-unnamed-export interface BadgeEnabledChangedCallback--><!--Device-unnamed-export interface BadgeEnabledChangedCallback-End-->

**System capability:** SystemCapability.Notification.Notification

## [[Call]]

```TypeScript
(data: EnabledNotificationCallbackData): void
```

Callback used to return the enabled state of the listened badge.

**Since:** 12

<!--Device-BadgeEnabledChangedCallback-(data: EnabledNotificationCallbackData): void--><!--Device-BadgeEnabledChangedCallback-(data: EnabledNotificationCallbackData): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [EnabledNotificationCallbackData](arkts-notification-notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | Yes | Callback used to return the enabled state of the listened badge. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let BadgeEnabledChangedCallback = (data: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info(`onBadgeEnabledChanged, badge enabled state change to: ${JSON.stringify(data)}`);
};
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeEnabledChanged: BadgeEnabledChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
