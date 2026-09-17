# getLauncherAbilityResourceInfoList (System API)

## Modules to Import

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getLauncherAbilityResourceInfoList

```TypeScript
function getLauncherAbilityResourceInfoList(optionsList: Array<BundleOptions>, resourceFlags: number): Promise<Array<LauncherAbilityResourceInfo>>
```

Obtains the launcher ability resource information of each application corresponding to the **BundleOptions** element in **optionsList**. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| optionsList | Array&lt;[BundleOptions](arkts-ability-bundleinfo-bundleoptions-i-sys.md)&gt; | Yes | Parameters of the applications to query.<br>**bundleName**, **moduleName**, and **abilityName** are mandatory parameters.<br>Value range of **appIndex**: [0, 5]. The default value is **0** if not specified.<br>**userId** is an invalid parameter. It does not need to be passed, and will not take effect if passed. |
| resourceFlags | number | Yes | Resource information flags, which indicate the type of resource information to obtain. The value is an enumerated value of [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md), excluding [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md).GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL and [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md).GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md)&gt;&gt; | Promise used to return the launcher ability resource information of the specified application list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle is not found. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The specified app index is invalid. |

**Examples**

```TypeScript
import { bundleManager, bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace the application information with the actual one.
let option: bundleManager.BundleOptions = {
  bundleName: 'com.example.demo',
  moduleName: 'entry',
  abilityName: 'EntryAbility',
  appIndex: 0
};

let optionsList: Array<bundleManager.BundleOptions> = [];
optionsList.push(option);
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getLauncherAbilityResourceInfoList(optionsList, resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList failed: %{public}s', message);
}
```
