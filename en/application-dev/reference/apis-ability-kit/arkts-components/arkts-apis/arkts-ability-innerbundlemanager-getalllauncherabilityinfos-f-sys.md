# getAllLauncherAbilityInfos (System API)

## Modules to Import

```TypeScript
import { innerBundleManager, BundleStatusCallback } from '@kit.AbilityKit';
```

## getAllLauncherAbilityInfos

```TypeScript
function getAllLauncherAbilityInfos(userId: number, callback: AsyncCallback<Array<LauncherAbilityInfo>>): void
```

Obtains the information about all launcher abilities. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md)(userId: number, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. The value must be greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-launcherabilityinfo-depr-i-sys.md)&gt;&gt; | Yes | Callback used to return an array of the launcher ability information. |


## getAllLauncherAbilityInfos

```TypeScript
function getAllLauncherAbilityInfos(userId: number): Promise<Array<LauncherAbilityInfo>>
```

Obtains the information about all launcher abilities. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md)(userId: number, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-launcherabilityinfo-depr-i-sys.md)&gt;&gt; | Promise used to return an array of the launcher ability information. |
