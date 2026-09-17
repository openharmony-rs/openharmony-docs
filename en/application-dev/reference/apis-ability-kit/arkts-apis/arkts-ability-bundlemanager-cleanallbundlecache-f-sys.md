# cleanAllBundleCache (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## cleanAllBundleCache

```TypeScript
function cleanAllBundleCache(): Promise<void>
```

Clears the global cache. This API uses a promise to return the result.

**Since:** 15

**Required permissions:** ohos.permission.REMOVE_CACHE_FILES

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.cleanAllBundleCache().then((data) => {
    hilog.info(0x0000, 'testTag', 'cleanAllBundleCache successful.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanAllBundleCache failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanAllBundleCache failed: %{public}s', message);
}
```
