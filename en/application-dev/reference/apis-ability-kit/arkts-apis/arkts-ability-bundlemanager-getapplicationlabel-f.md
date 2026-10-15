# getApplicationLabel

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getApplicationLabel

```TypeScript
function getApplicationLabel(bundleName: string, appIndex: number): Promise<string>
```

Obtains the app name based on the given bundle name and app index. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

<!--Device-bundleManager-function getApplicationLabel(bundleName: string, appIndex: int): Promise<string>--><!--Device-bundleManager-function getApplicationLabel(bundleName: string, appIndex: int): Promise<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| appIndex | number | Yes | Application index. The value ranges from 0 to 5, where 0 indicates the main application and 1 to 5 indicate the indexes of clone applications. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. If the call succeeds, it returns a list of application name; if the call fails, it returns an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The specified app index is invalid. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getApplicationLabel('com.hap.myapplication', 1).then((data: string) => {
    hilog.info(0x0000, 'testTag', 'getApplicationLabel succeed: Data: %{public}s', data);
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getApplicationLabel failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  hilog.error(0x0000, 'testTag', 'getApplicationLabel failed: error %{public}d  %{public}s', err.code, err.message);
}
```
