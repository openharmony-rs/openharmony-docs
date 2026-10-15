# getAllPreinstalledApplicationInfo (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllPreinstalledApplicationInfo

```TypeScript
function getAllPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>
```

Obtains the information about all preset applications. This API uses a promise to return the result. An empty array may be returned if the API call fails. Verify the return value before using it.

**Since:** 12

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>--><!--Device-bundleManager-function getAllPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PreinstalledApplicationInfo](arkts-ability-bundlemanager-preinstalledapplicationinfo-t-sys.md)&gt;&gt; | Promise used to return the result. If the call succeeds, it returns a list of PreinstalledApplicationInfo objects; if the call fails, it returns an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |

<!--Del-->
**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllPreinstalledApplicationInfo().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPreinstalledApplicationInfo success, Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllPreinstalledApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPreinstalledApplicationInfo failed: %{public}s', message);
}
```

<!--DelEnd-->
