# on (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## on('checkNotification')

```TypeScript
function on(type: 'checkNotification', callback: (checkInfo: NotificationCheckInfo) => NotificationCheckResult): void
```

Subscribes to notification events. The notification service sends the notification information in the callback to the verification program. The verification program returns the verification result to determine whether to publish the notification, for example, controlling the publication frequency of marketing notifications.

Each [SlotType](arkts-notification-notificationmanager-slottype-e.md) in the system can have only one registrant.

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-notificationManager-function on(type: 'checkNotification', callback: (checkInfo: NotificationCheckInfo) => NotificationCheckResult): void--><!--Device-notificationManager-function on(type: 'checkNotification', callback: (checkInfo: NotificationCheckInfo) => NotificationCheckResult): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'checkNotification' | Yes | Callback type. The value is fixed to **'checkNotification'**. |
| callback | (checkInfo: NotificationCheckInfo) =&gt; NotificationCheckResult | Yes | Pointer to the notification verification function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onCheckNotification = (info : notificationManager.NotificationCheckInfo): notificationManager.NotificationCheckResult => {
    console.info(`====>OnCheckNotification info: ${JSON.stringify(info)}`);
    if(info.notificationId == 1){
        let result: notificationManager.NotificationCheckResult =  { code: 1, message: 'testMsg1'};
        return result;
    } else {
        let result: notificationManager.NotificationCheckResult =   { code: 0, message: 'testMsg0'};
        return result;
    }
}
try{
    notificationManager.on('checkNotification', onCheckNotification);
} catch (err){
    console.error(`notificationManager.on failed, code is ${err.code}, message is ${err.message}`);
}
```

<!--DelEnd-->


## on('checkNotification')

```TypeScript
function on(type: 'checkNotification', checkRequest: NotificationCheckRequest,
    callback: (checkInfo: NotificationCheckInfo) => Promise<NotificationCheckResult>): void
```

Subscribes to notification events. The notification service sends the notification information in the callback to the verification program. The verification program returns the verification result to determine whether to publish the notification, for example, controlling the publication frequency of marketing notifications. This API uses a promise to return the result.

Each [SlotType](arkts-notification-notificationmanager-slottype-e.md) in the system can have only one registrant.

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-notificationManager-function on(type: 'checkNotification', checkRequest: NotificationCheckRequest,    callback: (checkInfo: NotificationCheckInfo) => Promise<NotificationCheckResult>): void--><!--Device-notificationManager-function on(type: 'checkNotification', checkRequest: NotificationCheckRequest,    callback: (checkInfo: NotificationCheckInfo) => Promise<NotificationCheckResult>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'checkNotification' | Yes | Callback type. The value is fixed to **'checkNotification'**. |
| checkRequest | [NotificationCheckRequest](arkts-notification-notificationmanager-notificationcheckrequest-t-sys.md) | Yes | [Notification request](../../../notification/notification-glossary.md#notification-request) content to be verified. |
| callback | (checkInfo: NotificationCheckInfo) =&gt; Promise&lt;[NotificationCheckResult](arkts-notification-notificationmanager-notificationcheckresult-i-sys.md)&gt; | Yes | Pointer to the notification verification function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
