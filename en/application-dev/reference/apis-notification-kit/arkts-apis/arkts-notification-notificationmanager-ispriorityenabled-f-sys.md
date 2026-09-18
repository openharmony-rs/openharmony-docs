# isPriorityEnabled (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isPriorityEnabled

```TypeScript
function isPriorityEnabled(): Promise<boolean>
```

Checks whether the priority notification is enabled.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result.<br> - **true**: The priority notification is enabled. <br> - **false**: The priority notification is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

notificationManager.isPriorityEnabled().then((result : boolean) => {
    hilog.info(0x0000, 'testTag', `isPriorityEnabled result is ${result}`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', `isPriorityEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```
