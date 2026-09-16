# DeviceModeDistributionPolicy（系统接口）

定义设备模式分发策略枚举，用于指定应用程序如何分发到设备上。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

未指定设备模式分发策略。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## MAIN_ONLY

```TypeScript
MAIN_ONLY = 1
```

该应用程序仅在主模式下可用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## SUB_ONLY

```TypeScript
SUB_ONLY = 2
```

该应用程序仅在副模式下可用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## UNIVERSAL_IDENTICAL_PACKAGE

```TypeScript
UNIVERSAL_IDENTICAL_PACKAGE = 3
```

应用程序在两种模式下都可用，具有相同的包体。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## UNIVERSAL_DIFFERENT_PACKAGE

```TypeScript
UNIVERSAL_DIFFERENT_PACKAGE = 4
```

应用程序在两种模式下都可用，具有不同的包体。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_IDENTICAL_PACKAGE = 5
```

该应用程序在不同模式之间以相同包体方式部分兼容。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE = 6
```

应用程序在不同模式之间以不同包体部分兼容。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## FULL_COMPATIBLE_IDENTICAL_PACKAGE

```TypeScript
FULL_COMPATIBLE_IDENTICAL_PACKAGE = 7
```

应用程序在不同模式之间以相同包体完全兼容。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## FULL_COMPATIBLE_DIFFERENT_PACKAGE

```TypeScript
FULL_COMPATIBLE_DIFFERENT_PACKAGE = 8
```

应用程序在不同模式之间以不同的包体方式完全兼容。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
