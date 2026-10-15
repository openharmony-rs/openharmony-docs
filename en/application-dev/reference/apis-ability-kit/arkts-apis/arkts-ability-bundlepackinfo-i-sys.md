# BundlePackInfo (System API)

```TypeScript
export interface BundlePackInfo
```

The module provides information in the **pack.info** file. The information can be obtained using [freeInstall.getBundlePackInfo](arkts-ability-freeinstall-getbundlepackinfo-f-sys.md).

**Since:** 9

<!--Device-unnamed-export interface BundlePackInfo--><!--Device-unnamed-export interface BundlePackInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## packages

```TypeScript
readonly packages: Array<PackageConfig>
```

Package configuration information in the **pack.info** file.

**Type:** Array&lt;[PackageConfig](arkts-ability-bundlepackinfo-packageconfig-i-sys.md)&gt;

**Since:** 9

<!--Device-BundlePackInfo-readonly packages: Array<PackageConfig>--><!--Device-BundlePackInfo-readonly packages: Array<PackageConfig>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## summary

```TypeScript
readonly summary: PackageSummary
```

Package summary information in the **pack.info** file.

**Type:** [PackageSummary](arkts-ability-bundlepackinfo-packagesummary-i-sys.md)

**Since:** 9

<!--Device-BundlePackInfo-readonly summary: PackageSummary--><!--Device-BundlePackInfo-readonly summary: PackageSummary-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
