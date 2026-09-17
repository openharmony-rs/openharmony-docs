# getAllBundleInfoByDeveloperId (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllBundleInfoByDeveloperId

```TypeScript
function getAllBundleInfoByDeveloperId(developerId: string): Array<BundleInfo>
```

Obtains the information about all bundles of the current user based on the given developer ID.

**Since:** 12

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| developerId | string | Yes | Developer ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[BundleInfo](arkts-ability-bundlemanager-bundleinfo-t.md)&gt; | An array of bundle information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter developerId is empty. |
| [17700059](../errorcode-bundle.md#17700059-specified-developer-id-does-not-exist) | The specified developerId is invalid. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let developerId = "123456.789";

try {
  let data = bundleManager.getAllBundleInfoByDeveloperId(developerId);
  hilog.info(0x0000, 'testTag', 'getAllBundleInfoByDeveloperId successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInfoByDeveloperId failed: %{public}s', message);
}
```
