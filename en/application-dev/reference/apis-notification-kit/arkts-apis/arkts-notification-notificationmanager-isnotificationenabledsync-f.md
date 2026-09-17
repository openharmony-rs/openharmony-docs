# isNotificationEnabledSync

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isNotificationEnabledSync

```TypeScript
function isNotificationEnabledSync(): boolean
```

Synchronously queries the notification authorization status of the current application.

This API is used to quickly check whether the current application is allowed to send notifications before publishing. It is synchronous and returns the result immediately after being called, suitable for scenarios where the enabled status needs to be obtained in a synchronous code flow.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**See also:**

[requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md) requests notification to be enabled for this application.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Result of the notification enabling status. The value **true** means that the notification is enabled, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
let enabled: boolean = notificationManager.isNotificationEnabledSync();
console.info(`isNotificationEnabledSync success, data is : ${JSON.stringify(enabled)}`);
```
