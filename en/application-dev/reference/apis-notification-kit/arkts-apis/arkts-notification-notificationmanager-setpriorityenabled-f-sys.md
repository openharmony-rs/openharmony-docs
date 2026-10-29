# setPriorityEnabled (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityEnabled

```TypeScript
function setPriorityEnabled(enable: boolean): Promise<void>
```

Sets the enabling status of the priority notification.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setPriorityEnabled(enable: boolean): Promise<void>--><!--Device-notificationManager-function setPriorityEnabled(enable: boolean): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether all notifications are allowed to be set as priority notifications. <br> - **true**: allows the notification to be set as a [priority notification](../../../notification/notification-glossary.md#priority-notification). <br> - **false**: forbids the notification from being set as a priority notification. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

notificationManager.setPriorityEnabled(false).then(() => {
    hilog.info(0x0000, 'testTag', `setPriorityEnabled success`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', `setPriorityEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
