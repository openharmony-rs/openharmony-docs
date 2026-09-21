# @ohos.bundle.bundleResourceManager

The module provides APIs for obtaining resource information, including [BundleResourceInfo](arkts-ability-bundleresourceinfo-i-sys.md) and [LauncherAbilityResourceInfo](arkts-ability-launcherabilityresourceinfo-i-sys.md).

> **NOTE:** 
> 
> Starting from API version 12, this module supports query of icons and names of disabled applications and
> applications installed by all users.
> 
> The APIs provided by this module are system APIs.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllBundleResourceInfo](arkts-ability-bundleresourcemanager-getallbundleresourceinfo-f-sys.md#getallbundleresourceinfo) | Obtains the bundle resource information of all applications based on the given resource flags. This API uses an asynchronous callback to return the result. |
| [getAllBundleResourceInfo](arkts-ability-bundleresourcemanager-getallbundleresourceinfo-f-sys.md#getallbundleresourceinfo-1) | Obtains the bundle resource information of all applications based on the given resource flags. This API uses a promise to return the result. |
| [getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md#getalllauncherabilityresourceinfo) | Obtains the resource information of the entry abilities of the current application based on the given resource flags. This API uses an asynchronous callback to return the result. |
| [getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md#getalllauncherabilityresourceinfo-1) | Obtains the resource information of the entry abilities of the current application based on the given resource flags. This API uses a promise to return the result. |
| [getAllUninstalledBundleResourceInfo](arkts-ability-bundleresourcemanager-getalluninstalledbundleresourceinfo-f-sys.md) | Obtains the bundle resource information of all uninstalled applications that have retained data based on the given resource flags. This API uses a promise to return the result. |
| [getBundleResourceInfo](arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getbundleresourceinfo) | Obtains the resource information of an application based on the given bundle name and resource flags. This API returns the result synchronously. |
| [getBundleResourceInfo](arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getbundleresourceinfo-1) | Obtains the resource information of an application based on the given bundle name, resource flags, and app index. This API returns the result synchronously. |
| [getExtensionAbilityResourceInfo](arkts-ability-bundleresourcemanager-getextensionabilityresourceinfo-f-sys.md) | Obtains the ExtensionAbility resource information of an application based on the bundle name, ExtensionAbility type, resource flags, and clone ID. This API returns the result synchronously. |
| [getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md#getlauncherabilityresourceinfo) | Obtains the bundle information of the entry ability of an application based on the given bundle name and resource flags. This API returns the result synchronously. |
| [getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md#getlauncherabilityresourceinfo-1) | Obtains the launcher ability resource information of an application based on the given bundle name, resource flags, and app index. This API returns the result synchronously. |
| [getLauncherAbilityResourceInfoList](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfolist-f-sys.md) | Obtains the launcher ability resource information of each application corresponding to the **BundleOptions** element in **optionsList**. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md) | Enumerates the resource information flags, which indicate the type of resource information to obtain. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [BundleResourceInfo](arkts-ability-bundleresourcemanager-bundleresourceinfo-t-sys.md) | Defines the icon and name of an application. |
| [LauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-launcherabilityresourceinfo-t-sys.md) | Defines the entry icon and name of an application. |
<!--DelEnd-->
