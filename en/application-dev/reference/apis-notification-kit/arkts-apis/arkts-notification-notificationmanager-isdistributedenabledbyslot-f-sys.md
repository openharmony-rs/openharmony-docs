# isDistributedEnabledBySlot (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isDistributedEnabledBySlot

```TypeScript
function isDistributedEnabledBySlot(slot: SlotType, deviceType: string): Promise<boolean>
```

Queries whether notifications of a specified slot can be sent to devices of a specified type. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Yes | Types of the notification slot. |
| deviceType | string | Yes | Device type.<br>Since API version 18, the following device types are supported:<br>- **headset**: wearable audio device<br>- **liteWearable**: lite wearable<br>- **wearable**: wearable<br>Since API version 20, the following device types are supported:<br>- **headset**: wearable audio device<br>- **liteWearable**: lite wearable<br>- **wearable**: wearable<br>- **current**: current device<br>- **2in1**: PC<br>- **tablet**: tablet |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that cross-device collaboration is supported, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let slot: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
let deviceType: string = 'wearable';

notificationManager.isDistributedEnabledBySlot(slot, deviceType).then((data: boolean) => {
    hilog.info(0x0000, 'testTag', '%{public}s', `isDistributedEnabledBySlot success.`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', '%{public}s', `isDistributedEnabledBySlot failed, code is ${err.code}, message is ${err.message}`);
});
```
