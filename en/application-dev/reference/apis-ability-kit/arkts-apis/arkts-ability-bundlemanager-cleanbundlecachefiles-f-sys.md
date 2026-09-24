# cleanBundleCacheFiles (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void
```

Clears the bundle cache based on the given bundle name. This API uses an asynchronous callback to return the result.

No permission is required when the caller clears its own cache.

**Since:** 9

**Required permissions:** ohos.permission.REMOVE_CACHE_FILES

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700030](../errorcode-bundle.md#17700030-failure-in-clearing-cache-files) | The specified bundle does not support clearing of cache files. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.cleanBundleCacheFiles(bundleName, err => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}
```


<a id="cleanbundlecachefiles-1"></a>

## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string): Promise<void>
```

Clears the bundle cache based on the given bundle name. This API uses a promise to return the result.

No permission is required when the caller clears its own cache.

**Since:** 9

**Required permissions:** ohos.permission.REMOVE_CACHE_FILES

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. If clearing the cache files fails, an error object is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700030](../errorcode-bundle.md#17700030-failure-in-clearing-cache-files) | The specified bundle does not support clearing of cache files. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.cleanBundleCacheFiles(bundleName).then(() => {
    hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}
```


<a id="cleanbundlecachefiles-2"></a>

## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, appIndex: number): Promise<void>
```

Clears the bundle cache based on the given bundle name and application index. This API uses a promise to return the result.

No permission is required when the caller clears its own cache.

**Since:** 15

**Required permissions:** ohos.permission.REMOVE_CACHE_FILES

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appIndex | number | Yes | Index of the application clone.<br>The value **0** means to clear the cache of the main application. A value greater than 0 means to clear the cache data of the application clone. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. If clearing the cache files fails, an error object is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700030](../errorcode-bundle.md#17700030-failure-in-clearing-cache-files) | The specified bundle does not support clearing of cache files. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";
let appIndex = 1;

try {
  bundleManager.cleanBundleCacheFiles(bundleName, appIndex).then(() => {
    hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}
```
