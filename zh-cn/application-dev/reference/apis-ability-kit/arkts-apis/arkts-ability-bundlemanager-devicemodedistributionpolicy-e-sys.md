# DeviceModeDistributionPolicy（系统接口）

```TypeScript
export enum DeviceModeDistributionPolicy
```

设备模式分发策略枚举，用于指定应用程序如何分发到设备上。

**起始版本：** 26.0.1

<!--Device-bundleManager-export enum DeviceModeDistributionPolicy--><!--Device-bundleManager-export enum DeviceModeDistributionPolicy-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## FULL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8
```

应用程序在不同模式之间完全兼容，具有不同的包体。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8--><!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## FULL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7
```

应用程序在不同模式之间完全兼容，具有相同的包体。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7--><!--Device-DeviceModeDistributionPolicy-FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## MAIN_ONLY

```TypeScript
MAIN_ONLY = 1
```

应用程序仅在主模式下可用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-MAIN_ONLY = 1--><!--Device-DeviceModeDistributionPolicy-MAIN_ONLY = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6
```

应用程序在不同模式之间部分兼容，具有不同的包体。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6--><!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5
```

应用程序在不同模式之间部分兼容，具有相同的包体。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5--><!--Device-DeviceModeDistributionPolicy-PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## SUB_ONLY

```TypeScript
SUB_ONLY = 2
```

应用程序仅在副模式下可用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-SUB_ONLY = 2--><!--Device-DeviceModeDistributionPolicy-SUB_ONLY = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## UNIVERSAL_DIFFERENT_PACKAGE

```TypeScript
UNIVERSAL_DIFFERENT_PACKAGE = 4
```

应用程序在两种模式下都可用，具有不同的包体。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-UNIVERSAL_DIFFERENT_PACKAGE = 4--><!--Device-DeviceModeDistributionPolicy-UNIVERSAL_DIFFERENT_PACKAGE = 4-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## UNIVERSAL_IDENTICAL_PACKAGE

```TypeScript
UNIVERSAL_IDENTICAL_PACKAGE = 3
```

应用程序在两种模式下都可用，具有相同的包体。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-UNIVERSAL_IDENTICAL_PACKAGE = 3--><!--Device-DeviceModeDistributionPolicy-UNIVERSAL_IDENTICAL_PACKAGE = 3-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

未指定设备模式分发策略。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceModeDistributionPolicy-UNSPECIFIED = 0--><!--Device-DeviceModeDistributionPolicy-UNSPECIFIED = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
