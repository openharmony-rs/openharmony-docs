# setSlotFlagsByBundle (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setSlotFlagsByBundle

```TypeScript
function setSlotFlagsByBundle(bundle: BundleOption, slotFlags: number): Promise<void>
```

Sets the slot flags for a specified application. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | Yes | Bundle information of the application. |
| slotFlags | number | Yes | Notification slot flags.<br>- Bit 0: sound alert. The value **0** means to disable the feature, and **1** means the opposite.<br>- Bit 1: locking the screen. The value **0** means to disable the feature, and **1** means the opposite.<br>- Bit 2: banner. The value **0** means to disable the feature, and **1** means the opposite.<br>- Bit 3: turning on the screen. The value **0** means to disable the feature, and **1** means the opposite.<br>- Bit 4: vibration. The value **0** means to disable the feature, and **1** means the opposite.<br>- Bit 5: notification icon in the status bar. The value **0** means to disable the feature, and **1** means the opposite. |

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
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle: notificationManager.BundleOption = {
    bundle: "bundleName1",
};

let slotFlags: number = 1;

notificationManager.setSlotFlagsByBundle(bundle, slotFlags).then(() => {
    console.info("setSlotFlagsByBundle success");
}).catch((err: BusinessError) => {
    console.error(`setSlotFlagsByBundle failed, code is ${err.code}, message is ${err.message}`);
});
```
