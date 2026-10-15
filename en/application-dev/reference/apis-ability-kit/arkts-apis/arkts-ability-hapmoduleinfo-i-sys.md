# HapModuleInfo

```TypeScript
export interface HapModuleInfo
```

The module defines the HAP module information. An application can obtain its own HAP module information through [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with **GET_BUNDLE_INFO_WITH_HAP_MODULE** passed in for [bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md).

**Since:** 9

<!--Device-unnamed-export interface HapModuleInfo--><!--Device-unnamed-export interface HapModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## codePhysicalPath

```TypeScript
readonly codePhysicalPath?: string
```

Indicates the physical installation path of the module.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-HapModuleInfo-readonly codePhysicalPath?: string--><!--Device-HapModuleInfo-readonly codePhysicalPath?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
