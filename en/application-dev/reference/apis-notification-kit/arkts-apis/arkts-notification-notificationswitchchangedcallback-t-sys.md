# NotificationSwitchChangedCallback (System API)

```TypeScript
export type NotificationSwitchChangedCallback = (callbackData: NotificationSwitchChangedCallbackData) => void
```

Registers the callback for notification switch state changes set by the [notificationManager.setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) API.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-export type NotificationSwitchChangedCallback = (callbackData: NotificationSwitchChangedCallbackData) => void--><!--Device-unnamed-export type NotificationSwitchChangedCallback = (callbackData: NotificationSwitchChangedCallbackData) => void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackData | [NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscriber-notificationswitchchangedcallbackdata-i-sys.md) | Yes | Callback that returns the notification switch state change information set by the [notificationManager.setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) API. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onNotificationSwitchChanged: (callbackData: notificationSubscribe.NotificationSwitchChangedCallbackData) => {
    console.info(`onNotificationSwitchChanged: ${JSON.stringify(callbackData)}`);
  }
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
