# isNotificationSlotEnabledByBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isNotificationSlotEnabledByBundles

```TypeScript
function isNotificationSlotEnabledByBundles(bundles: Array<BundleOption>, type: SlotType): Promise<Map<BundleOption, boolean>>
```

Checks whether a notification slot type is enabled for the specified applications in batch. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundles | Array&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)&gt; | Yes | Array of bundle information of the applications.<br>The maximum length is 1000 and cannot be empty. |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Yes | Notification slot type. All bundles share the same slot type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Map&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md), boolean&gt;&gt; | Promise used to return the result. The key is the bundle information, and the value **true** means that the notification slot type is enabled, and **false** means the opposite. Bundles whose slot has not been created will not appear in the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain whether the live view switch function is enabled for multiple applications in batches.
const bundles: Array<notificationManager.BundleOption> = [
    { bundle: 'com.example.app1', uid: 10001 },
    { bundle: 'com.example.app2', uid: 10002 },
];

notificationManager.isNotificationSlotEnabledByBundles(
    bundles, notificationManager.SlotType.LIVE_VIEW).then((data) => {
    data.forEach((value: boolean, key: notificationManager.BundleOption) => {
        console.info(`bundle: ${key.bundle}, enabled: ${value}`);
    });
}).catch((err: BusinessError) => {
    console.error(`isNotificationSlotEnabledByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```
