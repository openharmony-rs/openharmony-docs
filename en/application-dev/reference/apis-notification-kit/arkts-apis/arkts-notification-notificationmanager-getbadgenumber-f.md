# getBadgeNumber

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getBadgeNumber

```TypeScript
function getBadgeNumber(): Promise<number>
```

Obtains the badge number of this application. This API uses a promise to return the result.

This API is used to query the badge number displayed on the current application's desktop icon.

**Since:** 22

**System capability:** SystemCapability.Notification.Notification

**See also:**

[setBadgeNumber](arkts-notification-notificationmanager-setbadgenumber-f.md) sets the notification badge number.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the badge number. (The value is irrelevant to whether notifications and home-screen badges of this application are enabled.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getBadgeNumber().then((badgeNumber: number) => {
  console.info(`Succeeded in getting badge number, badgeNumber is ${JSON.stringify(badgeNumber)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get badge number. Code is ${err.code}, message is ${err.message}`);
});
```
