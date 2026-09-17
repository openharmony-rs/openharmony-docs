# getSubscribeInfo

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## getSubscribeInfo

```TypeScript
function getSubscribeInfo(): Promise<NotificationExtensionSubscriptionInfo[]>
```

Obtains the subscription information about the notification extension of this application. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.SUBSCRIBE_NOTIFICATION

**System capability:** SystemCapability.Notification.Notification

**See also:**

[subscribe](arkts-notification-notificationextensionsubscription-subscribe-f.md) subscribes from the notification extension.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscription-notificationextensionsubscriptioninfo-t.md)[]&gt; | Promise used to return the [NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscriptioninfo-i.md) array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
notificationExtensionSubscription.getSubscribeInfo().then((data: notificationExtensionSubscription.NotificationExtensionSubscriptionInfo[]) => {
  console.info(`getSubscribeInfo successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getSubscribeInfo fail, code is ${err.code}, message is ${err.message}`);
});
```
