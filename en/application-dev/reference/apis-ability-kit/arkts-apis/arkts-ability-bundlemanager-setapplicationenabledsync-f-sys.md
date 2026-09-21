# setApplicationEnabledSync (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setApplicationEnabledSync

```TypeScript
function setApplicationEnabledSync(bundleName: string, isEnabled: boolean): void
```

Enables or disables an application. This API returns the result synchronously.

**Since:** 10

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| isEnabled | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.setApplicationEnabledSync(bundleName, false);
  hilog.info(0x0000, 'testTag', 'setApplicationEnabledSync successfully.');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabledSync failed: %{public}s', message);
}
```


<a id="setapplicationenabledsync-1"></a>

## setApplicationEnabledSync

```TypeScript
function setApplicationEnabledSync(bundleName: string, appIndex: number, isEnabled: boolean, killProcess: boolean): void
```

Set whether an application is enabled or disabled, with control over whether the process is killed when disabled.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Indicates the bundle name. |
| appIndex | number | Yes | Indicates the index of clone app. |
| isEnabled | boolean | Yes | The value true means to enable the application, and the value false means to disable the application. |
| killProcess | boolean | Yes | The value true indicates that the application process will be killed when disabled, while the value false indicates that the application process will not be killed when disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Non-system APP calling system API. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The specified app index is invalid. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace with the application bundle name, application index, and whether to enable the application and whether to exit the application process when the application is disabled.
let bundleName: string = 'com.example.myapplication';
let appIndex: number = 0;
let isEnabled: boolean = true;
let killProcess: boolean = false;

try {
  bundleManager.setApplicationEnabledSync(bundleName, appIndex, isEnabled, killProcess);
  hilog.info(0x0000, 'testTag', 'setApplicationEnabledSync successfully');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabledSync failed: %{public}s', message);
}
```
