# ModuleInfo

```TypeScript
export interface ModuleInfo
```

The ModuleInfo module provides module information of an application.

> **NOTE:** 
> 
> This module is no longer maintained since API version 9. You are advised to use
> [bundleManager-HapModuleInfo](arkts-ability-hapmoduleinfo-depr-i.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [HapModuleInfo](arkts-ability-hapmoduleinfo-depr-i.md)

<!--Device-unnamed-export interface ModuleInfo--><!--Device-unnamed-export interface ModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

Module name.

**Type:** string

**Default:** Indicates the name of the .hap package to which the capability belongs

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

<!--Device-ModuleInfo-readonly moduleName: string--><!--Device-ModuleInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## moduleSourceDir

```TypeScript
readonly moduleSourceDir: string
```

Installation directory. Do not concatenate paths to access resource files. Use [resourceManager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager.md) to access resources.

**Type:** string

**Default:** Indicates the module source dir of this module

**Since:** 7

**Deprecated since:** 9

<!--Device-ModuleInfo-readonly moduleSourceDir: string--><!--Device-ModuleInfo-readonly moduleSourceDir: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework
