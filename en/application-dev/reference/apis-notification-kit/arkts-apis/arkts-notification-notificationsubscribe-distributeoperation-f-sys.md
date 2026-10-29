# distributeOperation (System API)

## Modules to Import

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## distributeOperation

```TypeScript
function distributeOperation(hashcode: string, operationInfo?: OperationInfo): Promise<void>
```

Triggers the [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) operation of the specified notification (for example, cross-device notification click-to-redirect and cross-device quick reply). This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function distributeOperation(hashcode: string, operationInfo?: OperationInfo): Promise<void>--><!--Device-notificationSubscribe-function distributeOperation(hashcode: string, operationInfo?: OperationInfo): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashcode | string | Yes | Unique notification ID. It is the value of **hashCode** in the [NotificationRequest](arkts-notification-notificationrequest-i.md) object of [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) used in the [onConsume](arkts-notification-notificationsubscriber-i-sys.md#onconsume) callback. |
| operationInfo | [OperationInfo](arkts-notification-notificationsubscribe-operationinfo-i-sys.md) | No | Cross-device collaboration operation information. When this parameter is not passed, the system default collaboration operation configuration is used. |

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
| [1600010](../errorcode-notification.md#1600010-distributed-operation-failed) | Distributed operation failed. |
| [1600021](../errorcode-notification.md#1600021-cross-device-communication-timeout) | Distributed operation timed out. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCode: string = 'hashCode';
let operationInfo: notificationSubscribe.OperationInfo = {
  actionName: 'actionName',
  userInput: 'userInput',
  operationType: 1,
  buttonIndex: 1,
};
notificationSubscribe.distributeOperation(hashCode, operationInfo).then(() => {
  console.info('distributeOperation success');
}).catch((err: BusinessError) => {
  console.error(`distributeOperation fail, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
