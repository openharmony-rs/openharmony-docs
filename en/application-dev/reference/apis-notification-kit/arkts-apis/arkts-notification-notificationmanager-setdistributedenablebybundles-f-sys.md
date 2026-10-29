# setDistributedEnableByBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setDistributedEnableByBundles

```TypeScript
function setDistributedEnableByBundles(bundleEnableInfos: Array<DistributedBundleEnableInfo>, deviceType: string): Promise<void>
```

Sets whether applications support [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) in batches. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setDistributedEnableByBundles(bundleEnableInfos: Array<DistributedBundleEnableInfo>, deviceType: string): Promise<void>--><!--Device-notificationManager-function setDistributedEnableByBundles(bundleEnableInfos: Array<DistributedBundleEnableInfo>, deviceType: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleEnableInfos | Array&lt;[DistributedBundleEnableInfo](arkts-notification-notificationmanager-distributedbundleenableinfo-i-sys.md)&gt; | Yes | Applications to set. |
| deviceType | string | Yes | Device type. <br>Since API version 18, the following device types are supported: <br>- **headset**: wearable audio device <br>- **liteWearable**: lite wearable <br>- **wearable**: wearable <br>Since API version 20, the following device types are supported: <br>- **headset**: wearable audio device <br>- **liteWearable**: lite wearable <br>- **wearable**: wearable <br>- **current**: current device <br>- **2in1**: PC <br>- **tablet**: tablet |

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
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600010](../errorcode-notification.md#1600010-distributed-operation-failed) | Distributed operation failed. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle1: notificationManager.DistributedBundleEnableInfo = {
    bundleName: 'bundleName1',
    uid: 1,
    enable: true
};
let bundle2: notificationManager.DistributedBundleEnableInfo = {
    bundleName: 'bundleName2',
    uid: 2,
    enable: true
};
let bundles: Array<notificationManager.DistributedBundleEnableInfo> = [
    bundle1,bundle2
]

let deviceType: string = 'liteWearable';
notificationManager.setDistributedEnableByBundles(bundles, deviceType).then(() => {
    console.info('setDistributedEnableByBundles success');
}).catch((err: BusinessError) => {
    console.error(`setDistributedEnableByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
