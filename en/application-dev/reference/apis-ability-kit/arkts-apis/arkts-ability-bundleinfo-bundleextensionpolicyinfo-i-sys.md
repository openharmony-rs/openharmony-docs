# BundleExtensionPolicyInfo (System API)

```TypeScript
export interface BundleExtensionPolicyInfo
```

Defines bundle extension policy information.

**Since:** 26.0.1

<!--Device-unnamed-export interface BundleExtensionPolicyInfo--><!--Device-unnamed-export interface BundleExtensionPolicyInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleExtensionPolicyInfo-readonly appIndex: int--><!--Device-BundleExtensionPolicyInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appSandboxPolicy

```TypeScript
readonly appSandboxPolicy: bundleManager.AppSandboxPolicy
```

The application sandbox policy.

**Type:** [bundleManager.AppSandboxPolicy](arkts-ability-bundlemanager-appsandboxpolicy-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleExtensionPolicyInfo-readonly appSandboxPolicy: bundleManager.AppSandboxPolicy--><!--Device-BundleExtensionPolicyInfo-readonly appSandboxPolicy: bundleManager.AppSandboxPolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleExtensionPolicyInfo-readonly bundleName: string--><!--Device-BundleExtensionPolicyInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## deviceModeDistributionPolicy

```TypeScript
readonly deviceModeDistributionPolicy: bundleManager.DeviceModeDistributionPolicy
```

The device mode distribution policy of the application.

**Type:** [bundleManager.DeviceModeDistributionPolicy](arkts-ability-bundlemanager-devicemodedistributionpolicy-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleExtensionPolicyInfo-readonly deviceModeDistributionPolicy: bundleManager.DeviceModeDistributionPolicy--><!--Device-BundleExtensionPolicyInfo-readonly deviceModeDistributionPolicy: bundleManager.DeviceModeDistributionPolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
