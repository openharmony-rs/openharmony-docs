# BundleInfo

```TypeScript
export interface BundleInfo
```

The module defines the bundle information.

**Since:** 9

<!--Device-unnamed-export interface BundleInfo--><!--Device-unnamed-export interface BundleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## appSandboxPolicy

```TypeScript
readonly appSandboxPolicy?: bundleManager.AppSandboxPolicy
```

App sandbox policy for dual-mode (2in1/tablet) scenarios.

**Type:** [bundleManager.AppSandboxPolicy](arkts-ability-bundlemanager-appsandboxpolicy-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly appSandboxPolicy?: bundleManager.AppSandboxPolicy--><!--Device-BundleInfo-readonly appSandboxPolicy?: bundleManager.AppSandboxPolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## deviceModeDistributionPolicy

```TypeScript
readonly deviceModeDistributionPolicy?: bundleManager.DeviceModeDistributionPolicy
```

Define the enumeration of device mode distribution policies, which is used to specify how an application is distributed on a device.

**Type:** [bundleManager.DeviceModeDistributionPolicy](arkts-ability-bundlemanager-devicemodedistributionpolicy-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly deviceModeDistributionPolicy?: bundleManager.DeviceModeDistributionPolicy--><!--Device-BundleInfo-readonly deviceModeDistributionPolicy?: bundleManager.DeviceModeDistributionPolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## sandboxCreatorBundleName

```TypeScript
readonly sandboxCreatorBundleName?: string
```

Bundle name of the sandbox application creator.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfo-readonly sandboxCreatorBundleName?: string--><!--Device-BundleInfo-readonly sandboxCreatorBundleName?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
