# getInstalledBundleList

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getInstalledBundleList

```TypeScript
function getInstalledBundleList(bundleFlags: number): Promise<Array<BundleInfo>>
```

Obtains all the bundle information in the system based on the given bundle flags. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_GET_INSTALLED_BUNDLE_LIST

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlags | number | Yes | Information contained in the returned BundleInfo. For details, see [BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleInfo](arkts-ability-bundlemanager-bundleinfo-t.md)&gt;&gt; | Promise used to return the list of installed applications. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

try {
  bundleManager.getInstalledBundleList(bundleFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getInstalledBundleList successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getInstalledBundleList failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getInstalledBundleList failed. Cause: %{public}s', message);
}
```
