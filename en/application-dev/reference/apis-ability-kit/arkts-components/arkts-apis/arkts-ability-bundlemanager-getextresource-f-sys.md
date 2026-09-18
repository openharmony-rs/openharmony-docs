# getExtResource (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getExtResource

```TypeScript
function getExtResource(bundleName: string): Promise<Array<string>>
```

Obtains the module names corresponding to the extended resources based on the given bundle name. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name based on which the extended resources are to be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the API call result and the module names corresponding to the extended resources. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700303](../errorcode-bundle.md#17700303-failed-to-obtain-extended-resources) | Failed to obtain extended resources. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';

try {
  bundleManager.getExtResource(bundleName).then((modules: Array<string>) => {
    for (let i = 0; i < modules.length; i++) {
      hilog.info(0x0000, 'testTag', 'getExtResource item: %{public}s', modules[i]);
    }
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getExtResource failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getExtResource failed. Cause: %{public}s', message);
}
```
