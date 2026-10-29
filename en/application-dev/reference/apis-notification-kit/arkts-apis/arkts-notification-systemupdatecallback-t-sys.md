# SystemUpdateCallback (System API)

```TypeScript
export type SystemUpdateCallback = (data: SubscribeCallbackData) => void
```

Returns the notification information carrying system property values.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-export type SystemUpdateCallback = (data: SubscribeCallbackData) => void--><!--Device-unnamed-export type SystemUpdateCallback = (data: SubscribeCallbackData) => void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | Yes | Notification information that carries the system property value. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onSystemUpdate: (data: notificationSubscribe.SubscribeCallbackData) => {
    let req = data.request;
    console.info(`onSystemUpdate callback req.priorityType: ${req.priorityNotificationType}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
