# ApplicationInfo

```TypeScript
export interface ApplicationInfo
```

The module defines the application information. An application can obtain its own application information through [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with **GET_BUNDLE_INFO_WITH_APPLICATION** passed in to [bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md).

**Since:** 9

<!--Device-unnamed-export interface ApplicationInfo--><!--Device-unnamed-export interface ApplicationInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## applicationReservedFlag

```TypeScript
readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag
```

Indicates the reserved flag of the application.

**Type:** [bundleManager.ApplicationReservedFlag](arkts-ability-bundlemanager-applicationreservedflag-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ApplicationInfo-readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag--><!--Device-ApplicationInfo-readonly applicationReservedFlag?: bundleManager.ApplicationReservedFlag-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## flags

```TypeScript
readonly flags?: number
```

Status set between the current application and the current user. Each bit indicates a specific Boolean status. For details about the values, see [ApplicationInfoFlag](arkts-ability-bundlemanager-applicationinfoflag-e-sys.md).

**Type:** number

**Since:** 12

<!--Device-ApplicationInfo-readonly flags?: int--><!--Device-ApplicationInfo-readonly flags?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
