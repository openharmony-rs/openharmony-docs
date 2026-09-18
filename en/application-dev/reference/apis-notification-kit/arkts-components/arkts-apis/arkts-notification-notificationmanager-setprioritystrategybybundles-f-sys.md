# setPriorityStrategyByBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityStrategyByBundles

```TypeScript
function setPriorityStrategyByBundles(strategies: Map<BundleOption, number>): Promise<void>
```

Sets the application priority notification strategies in batches. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategies | Map&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md), number&gt; | Yes | Key-value pair set of the application notification priority strategies. This parameter is obtained by performing the bitwise OR operation with the enumeration of [PriorityStrategyStatus](arkts-notification-notificationmanager-prioritystrategystatus-e-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
let strategies: Map<notificationManager.BundleOption, number> = new Map([[bundleOption, notificationManager.PriorityStrategyStatus.STATUS_APPLICATION_DEFINED]]);
notificationManager.setPriorityStrategyByBundles(strategies).then(() => {
  hilog.info(0x0000, 'testTag', `setPriorityStrategyByBundles success`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `setPriorityStrategyByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```
