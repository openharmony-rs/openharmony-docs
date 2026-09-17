# getAllNewPreinstalledApplicationInfo (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllNewPreinstalledApplicationInfo

```TypeScript
function getAllNewPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>
```

Obtains PreinstalledApplicationInfo of all newly added preinstalled applications during device OTA upgrade.

**Since:** 24

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PreinstalledApplicationInfo](arkts-ability-bundlemanager-preinstalledapplicationinfo-t-sys.md)&gt;&gt; | Returns a list of PreinstalledApplicationInfo objects. |

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
  bundleManager.getAllNewPreinstalledApplicationInfo().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllNewPreinstalledApplicationInfo success, Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllNewPreinstalledApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllNewPreinstalledApplicationInfo failed: %{public}s', message);
}
```
