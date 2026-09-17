# getAllSubscriptionBundles (System API)

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## getAllSubscriptionBundles

```TypeScript
function getAllSubscriptionBundles(): Promise<BundleOption[]>
```

Obtains all applications that have requested the ohos.permission.SUBSCRIBE_NOTIFICATION permission and implemented [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md). This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BundleOption](arkts-notification-notificationextensionsubscription-bundleoption-t.md)[]&gt; | Promise used to return the applications that have requested the ohos.permission.SUBSCRIBE_NOTIFICATION permission and implemented NotificationSubscriberExtensionAbility. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
notificationExtensionSubscription.getAllSubscriptionBundles().then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail, code is ${err.code}, message is ${err.message}`);
});
```
