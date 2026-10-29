# EnabledSilentReminderChangedCallback (System API)

```TypeScript
export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void
```

Triggered for registering the [silent reminder](../../../notification/notification-glossary.md#silent-reminder) enabled state change of application notifications.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void--><!--Device-unnamed-export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackData | [EnabledSilentReminderCallbackData](arkts-notification-notificationsubscriber-enabledsilentremindercallbackdata-i-sys.md) | Yes | Callback used to return the listened silent reminder enabled state. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onEnabledSilentReminderChangedCallback: notificationSubscribe.EnabledSilentReminderChangedCallback = (callbackData: notificationSubscribe.EnabledSilentReminderCallbackData) => {
  console.info('bundle: ', callbackData.bundle);
  console.info('uid: ', callbackData.uid);
  console.info('enable: ', callbackData.enableStatus);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledSilentReminderChanged: onEnabledSilentReminderChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
