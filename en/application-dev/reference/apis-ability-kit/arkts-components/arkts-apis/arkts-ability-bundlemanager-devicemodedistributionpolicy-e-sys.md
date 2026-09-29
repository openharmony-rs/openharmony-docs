# DeviceModeDistributionPolicy (System API)

```TypeScript
export enum DeviceModeDistributionPolicy
```

Define the enumeration of device mode distribution policies, which is used to specify how an application is distributed on a device.

**Since:** 26.0.1

<!--Device-bundleManager-export enum DeviceModeDistributionPolicy--><!--Device-bundleManager-export enum DeviceModeDistributionPolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

Unspecified device mode distribution policy.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-UNSPECIFIED = 0--><!--Device-DeviceModeDistributionPolicy-UNSPECIFIED = 0-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## MAIN_ONLY

```TypeScript
MAIN_ONLY = 1
```

The application is only available in primary mode.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-MAIN_ONLY = 1--><!--Device-DeviceModeDistributionPolicy-MAIN_ONLY = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## SUB_ONLY

```TypeScript
SUB_ONLY = 2
```

The application is only available in secondary mode.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-SUB_ONLY = 2--><!--Device-DeviceModeDistributionPolicy-SUB_ONLY = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## UNIVERSAL_IDENTICAL_PACKAGE

```TypeScript
UNIVERSAL_IDENTICAL_PACKAGE = 3
```

The application is available in both modes with identical package body.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-UNIVERSAL_IDENTICAL_PACKAGE = 3--><!--Device-DeviceModeDistributionPolicy-UNIVERSAL_IDENTICAL_PACKAGE = 3-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## UNIVERSAL_DIFFERENT_PACKAGE

```TypeScript
UNIVERSAL_DIFFERENT_PACKAGE = 4
```

The application is available in both modes with different package body.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-UNIVERSAL_DIFFERENT_PACKAGE = 4--><!--Device-DeviceModeDistributionPolicy-UNIVERSAL_DIFFERENT_PACKAGE = 4-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5
```

The application is partially compatible across modes with identical package body.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5--><!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6
```

The application is partially compatible across modes with different package body.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6--><!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## FULL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7
```

The application is fully compatible across modes with identical package body.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7--><!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## FULL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8
```

The application is fully compatible across modes with different package body.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8--><!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
