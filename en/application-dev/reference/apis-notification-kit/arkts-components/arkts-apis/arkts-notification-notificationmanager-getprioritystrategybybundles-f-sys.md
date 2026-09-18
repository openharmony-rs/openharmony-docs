# getPriorityStrategyByBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getPriorityStrategyByBundles

```TypeScript
function getPriorityStrategyByBundles(bundles: Array<BundleOption>): Promise<Map<BundleOption, number>>
```

Obtains the application priority notification strategies in batches. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundles | Array&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)&gt; | Yes | Array of application bundles. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Map&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md), number&gt;&gt; | Promise used to return the key-value pair set of the application notification priority strategies. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const bundleOption : notificationManager.BundleOption = { bundle: 'bundleName', uid: 1000 };
let bundles: Array<notificationManager.BundleOption> = new Array(bundleOption);
notificationManager.getPriorityStrategyByBundles(bundles).then((strategies: Map<notificationManager.BundleOption, number>) => {
  strategies.forEach((value, key) => {
    hilog.info(0x0000, 'testTag', `getPriorityStrategyByBundles strategies: ${key.bundle} ${key.uid}, ${value}`);
  })
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `getPriorityStrategyByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```
