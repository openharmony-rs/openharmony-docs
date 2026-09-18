# @ohos.bundle

The module provides APIs for obtaining information about an application, including bundle information, [application information](arkts-ability-applicationinfo-applicationinfo-depr-i.md#applicationinfo), and [ability information](arkts-ability-abilityinfo-abilityinfo-depr-i.md#abilityinfo). It also provides APIs to obtain and set the application disabling state.

> **NOTE:** 
> 
> The APIs of this module have been deprecated since API version 9. You are advised to use
> [@ohos.bundle.bundleManager](arkts-ability-bundle-bundlemanager.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [bundleManager](arkts-ability-bundle-bundlemanager.md)

**System capability:** SystemCapability.BundleManager.BundleFramework

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAbilityIcon](arkts-ability-bundle-getabilityicon-f.md) | Obtains the [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) of the icon corresponding to a given bundle name and ability name. This API uses an asynchronous callback to return the result. |
| [getAbilityIcon](arkts-ability-bundle-getabilityicon-f.md) | Obtains the [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) of the icon corresponding to a given bundle name and ability name. This API uses a promise to return the result. |
| [getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md) | Obtains the ability information based on a given bundle name and ability name. This API uses an asynchronous callback to return the result. |
| [getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md) | Obtains the ability information based on a given bundle name and ability name. This API uses a promise to return the result. |
| [getAbilityLabel](arkts-ability-bundle-getabilitylabel-f.md) | Obtains the application name based on a given bundle name and ability name. This API uses an asynchronous callback to return the result. |
| [getAbilityLabel](arkts-ability-bundle-getabilitylabel-f.md) | Obtains the application name based on a given bundle name and ability name. This API uses a promise to return the result. |
| [getAllApplicationInfo](arkts-ability-bundle-getallapplicationinfo-f.md) | Obtains the information about all applications. This API uses an asynchronous callback to return the result. |
| [getAllApplicationInfo](arkts-ability-bundle-getallapplicationinfo-f.md) | Obtains the information about all applications of the current user. This API uses an asynchronous callback to return the result. |
| [getAllApplicationInfo](arkts-ability-bundle-getallapplicationinfo-f.md) | Obtains the information about all applications of the specified user. This API uses a promise to return the result. |
| [getAllBundleInfo](arkts-ability-bundle-getallbundleinfo-f.md) | Obtains the information of all bundles of the specified user. This API uses an asynchronous callback to return the result. |
| [getAllBundleInfo](arkts-ability-bundle-getallbundleinfo-f.md) | Obtains the information of all bundles of the current user. This API uses an asynchronous callback to return the result. |
| [getAllBundleInfo](arkts-ability-bundle-getallbundleinfo-f.md) | Obtains the information of all bundles of the specified user. This API uses a promise to return the result. |
| [getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md) | Obtains the application information of the specified user based on a given bundle name. This API uses an asynchronous callback to return the result. |
| [getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md) | Obtains the application information based on a given bundle name. This API uses an asynchronous callback to return the result. |
| [getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md) | Obtains the application information based on a given bundle name. This API uses a promise to return the result. |
| [getBundleArchiveInfo](arkts-ability-bundle-getbundlearchiveinfo-f.md) | Obtains information about the bundles contained in a HAP file. This API uses an asynchronous callback to return the result. |
| [getBundleArchiveInfo](arkts-ability-bundle-getbundlearchiveinfo-f.md) | Obtains information about the bundles contained in a HAP file. This API uses a promise to return the result. |
| [getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md) | Obtains the bundle information based on a given bundle name and bundle options. This API uses an asynchronous callback to return the result. |
| [getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md) | Obtains the bundle information based on a given bundle name. This API uses an asynchronous callback to return the result. |
| [getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md) | Obtains the bundle information based on a given bundle name. This API uses a promise to return the result. |
| [getLaunchWantForBundle](arkts-ability-bundle-getlaunchwantforbundle-f.md) | Obtains the Want object that launches the specified application. This API uses an asynchronous callback to return the result. |
| [getLaunchWantForBundle](arkts-ability-bundle-getlaunchwantforbundle-f.md) | Obtains the Want object that launches the specified application. This API uses a promise to return the result. |
| [getNameForUid](arkts-ability-bundle-getnameforuid-f.md) | Obtains bundle name by the given uid. |
| [getNameForUid](arkts-ability-bundle-getnameforuid-f.md) | Obtains the bundle name based on a UID. This API uses a promise to return the result. |
| [isAbilityEnabled](arkts-ability-bundle-isabilityenabled-f.md) | Checks whether the ability that matches a given AbilityInfo object is enabled. This API uses an asynchronous callback to return the result. |
| [isAbilityEnabled](arkts-ability-bundle-isabilityenabled-f.md) | Checks whether the ability that matches a given AbilityInfo object is enabled. This API uses a promise to return the result. |
| [isApplicationEnabled](arkts-ability-bundle-isapplicationenabled-f.md) | Checks whether an application is enabled based on a given bundle name. This API uses an asynchronous callback to return the result. |
| [isApplicationEnabled](arkts-ability-bundle-isapplicationenabled-f.md) | Checks whether an application is enabled based on a given bundle name. This API uses a promise to return the result. |
| [queryAbilityByWant](arkts-ability-bundle-queryabilitybywant-f.md) | Obtains the ability information of the specified user based on given Want. This API uses an asynchronous callback to return the result. |
| [queryAbilityByWant](arkts-ability-bundle-queryabilitybywant-f.md) | Obtains the ability information based on given Want. This API uses an asynchronous callback to return the result. |
| [queryAbilityByWant](arkts-ability-bundle-queryabilitybywant-f.md) | Obtains the ability information based on given Want. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cleanBundleCacheFiles](arkts-ability-bundle-cleanbundlecachefiles-f-sys.md) | Clears the cache data of an application. This API uses an asynchronous callback to return the result. |
| [cleanBundleCacheFiles](arkts-ability-bundle-cleanbundlecachefiles-f-sys.md) | Clears the cache data of an application. This API uses a promise to return the result. |
| [getApplicationInfos](arkts-ability-bundle-getapplicationinfos-f-sys.md) | Obtains information about all installed apps for a specified user. This API uses an asynchronous callback to return the result. |
| [getApplicationInfos](arkts-ability-bundle-getapplicationinfos-f-sys.md) | Obtains information about installed apps for the user to which the caller belongs. This API uses an asynchronous callback to return the result. |
| [getApplicationInfos](arkts-ability-bundle-getapplicationinfos-f-sys.md) | Obtains information about all installed apps for a specified user. This API uses a promise to return the result. |
| [getBundleInfos](arkts-ability-bundle-getbundleinfos-f-sys.md) | Obtains all BundleInfo for a specified user in the system. This API uses an asynchronous callback to return the result. |
| [getBundleInfos](arkts-ability-bundle-getbundleinfos-f-sys.md) | Obtains all BundleInfo for the current user. This API uses an asynchronous callback to return the result. |
| [getBundleInfos](arkts-ability-bundle-getbundleinfos-f-sys.md) | Obtains all BundleInfo for a specified user. This API uses a promise to return the result. |
| [getBundleInstaller](arkts-ability-bundle-getbundleinstaller-f-sys.md) | Obtains the installation package. This API uses an asynchronous callback to return the result. |
| [getBundleInstaller](arkts-ability-bundle-getbundleinstaller-f-sys.md) | Obtains the installation package. This API uses a promise to return the result. |
| [getPermissionDef](arkts-ability-bundle-getpermissiondef-f-sys.md) | Obtains the permission details by permission name. This API uses an asynchronous callback to return the result. |
| [getPermissionDef](arkts-ability-bundle-getpermissiondef-f-sys.md) | Obtains the permission details by permission name. This API uses a promise to return the result. |
| [setAbilityEnabled](arkts-ability-bundle-setabilityenabled-f-sys.md) | Sets whether to enable an ability. This API uses an asynchronous callback to return the result. |
| [setAbilityEnabled](arkts-ability-bundle-setabilityenabled-f-sys.md) | Sets whether to enable an ability. This API uses a promise to return the result. |
| [setApplicationEnabled](arkts-ability-bundle-setapplicationenabled-f-sys.md) | Sets whether to enable an application. This API uses an asynchronous callback to return the result. |
| [setApplicationEnabled](arkts-ability-bundle-setapplicationenabled-f-sys.md) | Sets whether to enable an application. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BundleOptions](arkts-ability-bundle-bundleoptions-i.md) |  |

### Enums

| Name | Description |
| --- | --- |
| [AbilitySubType](arkts-ability-bundle-abilitysubtype-e.md) |  |
| [AbilityType](arkts-ability-bundle-abilitytype-e.md) |  |
| [BundleFlag](arkts-ability-bundle-bundleflag-e.md) |  |
| [ColorMode](arkts-ability-bundle-colormode-e.md) |  |
| [DisplayOrientation](arkts-ability-bundle-displayorientation-e.md) |  |
| [GrantStatus](arkts-ability-bundle-grantstatus-e.md) |  |
| [InstallErrorCode](arkts-ability-bundle-installerrorcode-e.md) |  |
| [LaunchMode](arkts-ability-bundle-launchmode-e.md) |  |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ModuleRemoveFlag](arkts-ability-bundle-moduleremoveflag-e-sys.md) | Flag indicating whether a module is associated with a widget or shortcut when it is removed. |
| [QueryShortCutFlag](arkts-ability-bundle-queryshortcutflag-e-sys.md) | Flag used to specify the query scope for shortcuts. |
| [ShortcutExistence](arkts-ability-bundle-shortcutexistence-e-sys.md) | Result returned when querying whether a shortcut exists. |
| [SignatureCompareResult](arkts-ability-bundle-signaturecompareresult-e-sys.md) | Signature verification result. |
<!--DelEnd-->
