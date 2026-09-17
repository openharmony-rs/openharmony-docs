# setTargetDeviceStatus (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setTargetDeviceStatus

```TypeScript
function setTargetDeviceStatus(deviceType: string, status: number): Promise<void>
```

Sets the status of a device after it is successfully connected. Device status determines the notification mode of the current device when a notification is published.

**Since:** 18

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | string | Yes | Device type. Currently, only **headset**, **liteWearable**, **wearable**, **glasses**, and **current** are supported. |
| status | number | Yes | Device status.<br>- Bit 0: whether the device is in use. The value **0** indicates that the device is available; **1** indicates that the device is in use.<br>- Bit 1: whether the device user is the owner. The value **0** indicates that the user is not the owner; **1** indicates the opposite.<br>- Bit 2: whether the device is in the Do Not Disturb mode. The value **0** indicates that the device is not in the Do Not Disturb mode; **1** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.setTargetDeviceStatus("current", 1).then(() => {
  console.info(`Succeeded in setting target device status.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set target device status. Code is ${err.code}, message is ${err.message}`);
});
```
