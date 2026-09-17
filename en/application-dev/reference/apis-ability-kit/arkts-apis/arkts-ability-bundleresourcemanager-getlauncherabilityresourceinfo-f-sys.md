# getLauncherAbilityResourceInfo (System API)

## Modules to Import

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getLauncherAbilityResourceInfo

```TypeScript
function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: number): Array<LauncherAbilityResourceInfo>
```

Obtains the bundle information of the entry ability of an application based on the given bundle name and resource flags. This API returns the result synchronously.

**Since:** 11

**Required permissions:** ohos.permission.GET_BUNDLE_RESOURCES

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| resourceFlags | number | No | Type of the resource information to obtain. The default value is **[ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md).GET_RESOURCE_INFO_ALL**. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md)&gt; | Resource information of the entry ability obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |

**Examples**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getLauncherAbilityResourceInfo(bundleName, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
let appIndex = 1;
try {
  let resourceInfo = bundleResourceManager.getLauncherAbilityResourceInfo(bundleName, resourceFlag, appIndex);
  hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfo failed: %{public}s', message);
}
```


## getLauncherAbilityResourceInfo

```TypeScript
function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: number, appIndex?: number): Array<LauncherAbilityResourceInfo>
```

Obtains the launcher ability resource information of an application based on the given bundle name, resource flags, and app index. This API returns the result synchronously.

**Since:** 12

**Required permissions:** ohos.permission.GET_BUNDLE_RESOURCES

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| resourceFlags | number | No | Type of the resource information to obtain. The default value is **[ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md).GET_RESOURCE_INFO_ALL**. |
| appIndex | number | No | Index of the application clone. The default value is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md)&gt; | Resource information of the entry ability obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range or not found. |

**Examples**

See [getLauncherAbilityResourceInfo](#getlauncherabilityresourceinfo)
