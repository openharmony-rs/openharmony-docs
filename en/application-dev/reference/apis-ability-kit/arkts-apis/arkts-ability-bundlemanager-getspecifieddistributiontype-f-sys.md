# getSpecifiedDistributionType (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getSpecifiedDistributionType

```TypeScript
function getSpecifiedDistributionType(bundleName: string): string
```

Synchronously queries the [HarmonyAppProvision Configuration File](../../../security/app-provision-structure.md) of a specified bundle name. The return value is the specifiedDistributionType field in the [InstallParam](arkts-ability-installer-installparam-i-sys.md) passed when the install API is called.

No permission is required for obtaining the caller's own information.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getSpecifiedDistributionType(bundleName: string): string--><!--Device-bundleManager-function getSpecifiedDistributionType(bundleName: string): string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| string | [HarmonyAppProvision Configuration File](../../../security/app-provision-structure.md) of the specified bundle name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |

<!--Del-->
**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";

try {
  let type = bundleManager.getSpecifiedDistributionType(bundleName);
  hilog.info(0x0000, 'testTag', 'getSpecifiedDistributionType successfully, type:%{public}s', type);
} catch (error) {
  let message = (error as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSpecifiedDistributionType failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
