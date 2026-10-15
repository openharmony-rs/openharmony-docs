# subscribeNotification (System API)

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## subscribeNotification

```TypeScript
function subscribeNotification(priorityStrategy?: number): Promise<void>
```

Subscribes to notifications based on the priority strategy. This API uses a promise to return the result.

**Since:** 26.2.0

**Required permissions:** ohos.permission.NOTIFICATION_SYSTEM_SUBSCRIBER

**Model restriction:** This API can be used only in the stage model.

<!--Device-notificationExtensionSubscription-function subscribeNotification(priorityStrategy?: int): Promise<void>--><!--Device-notificationExtensionSubscription-function subscribeNotification(priorityStrategy?: int): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| priorityStrategy | number | No | Priority strategy for filtering the notifications. This parameter is obtained by performing a bitwise OR operation on the enums of PriorityStrategyStatus. After an application subscribes to a specific priority strategy, the system returns only notifications matching the corresponding strategy when the application publishes notifications. Subscribing to the default priority strategy **STATUS_SYSTEM_DEFAULT** means subscribing simultaneously to the following strategies: **STATUS_SYSTEM_RULE**, **STATUS_INTELLIGENT**, **STATUS_USER_DEFINED**, and **STATUS_APPLICATION_DEFINED**. When **priorityStrategy** is set to **0**, no priority strategy is applied, and all notifications published by the application can be received.<br>The value should be an integer. Default value: 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.The user does not exist. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-invalid-bundle-information) | The application does not implement the NotificationSubscriberExtensionAbility. |
