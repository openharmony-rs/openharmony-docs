# getBundleInstallStatus

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getBundleInstallStatus

```TypeScript
function getBundleInstallStatus(bundleName: string): BundleInstallStatus
```

Obtains the installation status of a specified application under a given user.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| [BundleInstallStatus](arkts-ability-bundlemanager-bundleinstallstatus-e.md) | Application installation status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API.<br>**Applicable version:** 23 - 26.0.0 |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace it with the actual bundle name.
let bundleName: string = 'com.ohos.demo';

try {
  let bundleInstallStatus = bundleManager.getBundleInstallStatus(bundleName);
  hilog.info(0x0000, 'testTag', 'bundle install status:' + bundleInstallStatus);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInstallStatus failed. Cause: %{public}s', message);
}
```
