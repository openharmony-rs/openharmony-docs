# @ohos.bundle.freeInstall

The module provides APIs for setting and obtaining installation-free information and APIs for obtaining
 BundlePackInfo and DispatchInfo.

> **NOTE**
 >
 > The APIs provided by this module are system APIs.


**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { freeInstall } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getBundlePackInfo](arkts-ability-freeinstall-getbundlepackinfo-f-sys.md) | Obtains bundlePackInfo based on **bundleName** and **bundlePackFlag**. This API uses an asynchronous callback to return the result. |
| [getBundlePackInfo](arkts-ability-freeinstall-getbundlepackinfo-f-sys.md) | Obtains bundlePackInfo based on **bundleName** and **bundlePackFlag**. This API uses a promise to return the result. |
| [getDispatchInfo](arkts-ability-freeinstall-getdispatchinfo-f-sys.md) | Obtains the dispatch information. This API uses an asynchronous callback to return the result. |
| [getDispatchInfo](arkts-ability-freeinstall-getdispatchinfo-f-sys.md) | Obtains the dispatch information. This API uses a promise to return the result. |
| [isHapModuleRemovable](arkts-ability-freeinstall-ishapmoduleremovable-f-sys.md) | Checks whether a module can be removed. This API uses an asynchronous callback to return the result. |
| [isHapModuleRemovable](arkts-ability-freeinstall-ishapmoduleremovable-f-sys.md) | Checks whether a module can be removed. This API uses a promise to return the result. |
| [setHapModuleUpgradeFlag](arkts-ability-freeinstall-sethapmoduleupgradeflag-f-sys.md) | Sets an upgrade flag for a module. This API uses an asynchronous callback to return the result. |
| [setHapModuleUpgradeFlag](arkts-ability-freeinstall-sethapmoduleupgradeflag-f-sys.md) | Sets an upgrade flag for a module. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [BundlePackFlag](arkts-ability-freeinstall-bundlepackflag-e-sys.md) | Flag of the bundle package. |
| [UpgradeFlag](arkts-ability-freeinstall-upgradeflag-e-sys.md) | Upgrade flag, which is for internal use only. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AbilityFormInfo](arkts-ability-freeinstall-abilityforminfo-t-sys.md) | Defines the widget information. |
| [ApiVersion](arkts-ability-freeinstall-apiversion-t-sys.md) | Defines the API version of the module. |
| [BundleConfigInfo](arkts-ability-freeinstall-bundleconfiginfo-t-sys.md) | Defines the bundle configuration information. |
| [BundlePackInfo](arkts-ability-freeinstall-bundlepackinfo-t-sys.md) | Defines the bundle information. |
| [DispatchInfo](arkts-ability-freeinstall-dispatchinfo-t-sys.md) | Defines the installation-free structure and API version information. |
| [ExtensionAbility](arkts-ability-freeinstall-extensionability-t-sys.md) | Defines the ExtensionAbility configuration information. |
| [ModuleAbilityInfo](arkts-ability-freeinstall-moduleabilityinfo-t-sys.md) | Defines the ability information of the module. |
| [ModuleConfigInfo](arkts-ability-freeinstall-moduleconfiginfo-t-sys.md) | Defines the module configuration information of the bundle. |
| [ModuleDistroInfo](arkts-ability-freeinstall-moduledistroinfo-t-sys.md) | Defines the distribution information of the module. |
| [PackageConfig](arkts-ability-freeinstall-packageconfig-t-sys.md) | Defines the package configuration information in the **pack.info** file. |
| [PackageSummary](arkts-ability-freeinstall-packagesummary-t-sys.md) | Defines the package summary information in the **pack.info** file. |
| [Version](arkts-ability-freeinstall-version-t-sys.md) | Defines the version in the **pack.info** file. |
<!--DelEnd-->
