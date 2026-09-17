# DeviceModeDistributionPolicy (System API)

Define the enumeration of device mode distribution policies, which is used to specify how an application is distributed on a device.

**Since:** 26.1.0

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

Unspecified device mode distribution policy.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## MAIN_ONLY

```TypeScript
MAIN_ONLY = 1
```

The application is only available in primary mode.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## SUB_ONLY

```TypeScript
SUB_ONLY = 2
```

The application is only available in secondary mode.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## UNIVERSAL_IDENTICAL_PACKAGE

```TypeScript
UNIVERSAL_IDENTICAL_PACKAGE = 3
```

The application is available in both modes with identical package body.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## UNIVERSAL_DIFFERENT_PACKAGE

```TypeScript
UNIVERSAL_DIFFERENT_PACKAGE = 4
```

The application is available in both modes with different package body.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5
```

The application is partially compatible across modes with identical package body.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6
```

The application is partially compatible across modes with different package body.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## FULL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7
```

The application is fully compatible across modes with identical package body.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## FULL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8
```

The application is fully compatible across modes with different package body.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
