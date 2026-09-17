# snoozeNotification (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## snoozeNotification

```TypeScript
function snoozeNotification(hashCode: string, delayTime: number): Promise<void>
```

Snoozes a notification. The notification will be reminded again after the specified time. Each setting will trigger only one reminder, and the reminder mode will be the same as that of the notification.<br>The notification will be deleted after the setting.

**Since:** 26.0.0

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCode | string | Yes | Unique ID of the notification to be snoozed. |
| delayTime | number | Yes | Interval for the snoozed notification.<br>Unit: second. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [1600028](../errorcode-notification.md#1600028-current-notification-does-not-support-this-api) | This notification is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Replace it with the unique ID of the notification to be snoozed.
let hashCode: string = "hashCode";
let delayTime: number = 60;
notificationManager.snoozeNotification(hashCode, delayTime).then(() => {
  console.info("snoozeNotification success.")
}).catch((err: BusinessError):void => {
  console.error(`snoozeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```
