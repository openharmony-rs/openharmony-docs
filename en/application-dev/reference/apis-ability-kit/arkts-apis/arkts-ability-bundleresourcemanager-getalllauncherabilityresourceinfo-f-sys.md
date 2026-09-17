# getAllLauncherAbilityResourceInfo (System API)

## Modules to Import

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getAllLauncherAbilityResourceInfo

```TypeScript
function getAllLauncherAbilityResourceInfo(resourceFlags: number, callback: AsyncCallback<Array<LauncherAbilityResourceInfo>>): void
```

Obtains the resource information of the entry abilities of the current application based on the given resource flags. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceFlags | number | Yes | Type of the resource information to obtain. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the information is successfully obtained, **err** is **null** and **data** is a LauncherAbilityResourceInfo array. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
      return;
    }
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```


## getAllLauncherAbilityResourceInfo

```TypeScript
function getAllLauncherAbilityResourceInfo(resourceFlags: number): Promise<Array<LauncherAbilityResourceInfo>>
```

Obtains the resource information of the entry abilities of the current application based on the given resource flags. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceFlags | number | Yes | Type of the resource information to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md)&gt;&gt; | Promise used to return the LauncherAbilityResourceInfo array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

See [getAllLauncherAbilityResourceInfo](#getalllauncherabilityresourceinfo)
