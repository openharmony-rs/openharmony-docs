# getNotificationSwitchLimitedBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getNotificationSwitchLimitedBundles

```TypeScript
function getNotificationSwitchLimitedBundles(userId: number): Promise<Map<string, boolean>>
```

Obtains the list of apps whose notification permission is restricted. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

<!--Device-notificationManager-function getNotificationSwitchLimitedBundles(userId: int): Promise<Map<string, boolean>>--><!--Device-notificationManager-function getNotificationSwitchLimitedBundles(userId: int): Promise<Map<string, boolean>>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. <br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Map&lt;string, boolean&gt;&gt; | Promise used to return a collection of key-value pairs indicating the status of the application notification switch. <br> - **true**: enabled. <br> - **false**: disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
