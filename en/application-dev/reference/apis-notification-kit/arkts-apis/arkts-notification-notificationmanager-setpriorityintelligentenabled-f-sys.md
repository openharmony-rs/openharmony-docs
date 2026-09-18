# setPriorityIntelligentEnabled (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityIntelligentEnabled

```TypeScript
function setPriorityIntelligentEnabled(enable: boolean): Promise<void>
```

Sets the enabling status of the intelligent priority notification service. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Enabling status of the intelligent priority notification service.<br> - **true**: The intelligent priority notification service is enabled.<br> - **false**: The intelligent priority notification service is disabled. |

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
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

notificationManager.setPriorityIntelligentEnabled(false).then(() => {
  hilog.info(0x0000, 'testTag', `setPriorityIntelligentEnabled success`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `setPriorityIntelligentEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```
