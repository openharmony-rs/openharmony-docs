# getActiveNotification (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getActiveNotification

```TypeScript
function getActiveNotification(hashCode: string): Promise<NotificationRequest>
```

Obtains an active notification based on **hashCode**. This API uses a promise to return the result.

**Since:** 26.2.0

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

<!--Device-notificationManager-function getActiveNotification(hashCode: string): Promise<NotificationRequest>--><!--Device-notificationManager-function getActiveNotification(hashCode: string): Promise<NotificationRequest>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCode | string | Yes | Unique notification identifier. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md)&gt; | Promise used to return the notification information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.The user does not exist. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotification().then((data: notificationManager.NotificationRequest) => {
    console.info(`getActiveNotification success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveNotification failed, code is ${err.code}, message is ${err.message}`);
});
```
