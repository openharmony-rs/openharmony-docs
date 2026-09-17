# isUserGranted

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## isUserGranted

```TypeScript
function isUserGranted(): Promise<boolean>
```

Checks whether the **Allow access to notifications on this device** switch is toggled on. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.SUBSCRIBE_NOTIFICATION

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that this feature is enabled, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
notificationExtensionSubscription.isUserGranted().then((isOpen: boolean) => {
  if (isOpen) {
    console.info('isUserGranted true');
  } else {
    console.info('isUserGranted false');
  }
}).catch((err: BusinessError) => {
  console.error(`isUserGranted fail, code is ${err.code}, message is ${err.message}`);
});
```
