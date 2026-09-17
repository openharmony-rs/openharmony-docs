# isSmartReminderEnabled (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isSmartReminderEnabled

```TypeScript
function isSmartReminderEnabled(deviceType: string): Promise<boolean>
```

Obtains a smart reminder for cross-device collaboration. This API uses a promise to return the result.

This API can be properly called on devices other than wearables and TVs. If it is called on wearables and TVs, error code 801 is returned.

**Since:** 12

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | string | Yes | Device type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result (**true**: enabled; **false**: disabled). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600010](../errorcode-notification.md#1600010-distributed-operation-failed) | Distributed operation failed. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let deviceType: string = "phone";
notificationManager.isSmartReminderEnabled(deviceType).then((data: boolean) => {
    console.info(`isSmartReminderEnabled success, data:${data}`);
}).catch((err: BusinessError) => {
    console.error(`isSmartReminderEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```
