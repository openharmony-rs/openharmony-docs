# setPriorityEnabledByBundle (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityEnabledByBundle

```TypeScript
function setPriorityEnabledByBundle(bundle: BundleOption, enableStatus: PriorityEnableStatus): Promise<void>
```

Sets the enabling status of the priority notification for an application.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | Yes | Bundle information of the application. |
| enableStatus | [PriorityEnableStatus](arkts-notification-notificationmanager-priorityenablestatus-e-sys.md) | Yes | Whether the priority notification for an application is enabled.<br>   - **DISABLE**: The priority notification is disabled.<br> - **ENABLE_BY_INTELLIGENT**: The priority   notification can be enabled through intelligent recognition, user keyword matching, or application rule matching.<br> - **ENABLE**: The priority notification is enabled for all applications. |

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
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const bundleOption : notificationManager.BundleOption = { bundle: 'bundleName', uid: 0 };
notificationManager.setPriorityEnabledByBundle(bundleOption, notificationManager.PriorityEnableStatus.ENABLE).then(() => {
  hilog.info(0x0000, 'testTag', `setPriorityEnabledByBundle success`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `setPriorityEnabledByBundle failed, code is ${err.code}, message is ${err.message}`);
});
```
