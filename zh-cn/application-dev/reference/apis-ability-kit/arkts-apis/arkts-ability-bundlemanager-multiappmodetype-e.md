# MultiAppModeType

标识应用多开的模式类型。

**起始版本：** 12

<!--Device-bundleManager-export enum MultiAppModeType--><!--Device-bundleManager-export enum MultiAppModeType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

未指定类型，表示[multiAppMode配置](../../../quick-start/app-configuration-file.md#multiappmode标签)未配置时的默认状态。

**起始版本：** 12

<!--Device-MultiAppModeType-UNSPECIFIED = 0--><!--Device-MultiAppModeType-UNSPECIFIED = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## MULTI_INSTANCE

```TypeScript
MULTI_INSTANCE = 1
```

[多实例模式](../../../quick-start/multiInstance.md)。常驻进程不支持该字段。

**起始版本：** 12

<!--Device-MultiAppModeType-MULTI_INSTANCE = 1--><!--Device-MultiAppModeType-MULTI_INSTANCE = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## APP_CLONE

```TypeScript
APP_CLONE = 2
```

[分身模式](../../../quick-start/app-clone.md)。

**起始版本：** 12

<!--Device-MultiAppModeType-APP_CLONE = 2--><!--Device-MultiAppModeType-APP_CLONE = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

