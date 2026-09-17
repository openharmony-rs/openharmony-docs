# setNotificationSwitch (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setNotificationSwitch

```TypeScript
function setNotificationSwitch(switchName: string, switchState: boolean, userId: number): Promise<void>
```

Sets the notification switch state. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| switchName | string | Yes | Name of the notification switch. The value can be **DEAL** (aggregated switch for transaction notifications) or **LOGISTICS** (aggregated switch for logistics notifications). |
| switchState | boolean | Yes | Whether to enable the notification switch.<br> - **true**: enable. <br> - **false**: disable. |
| userId | number | Yes | User ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. Database operation failed. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let switchName: string = 'DEAL';
let switchState: boolean = true;
let userId: number = 100;

notificationManager.setNotificationSwitch(switchName, switchState, userId).then(() => {
    console.info('setNotificationSwitch success');
}).catch((err: BusinessError) => {
    console.error(`setNotificationSwitch failed, code is ${err.code}, message is ${err.message}`);
});
```
