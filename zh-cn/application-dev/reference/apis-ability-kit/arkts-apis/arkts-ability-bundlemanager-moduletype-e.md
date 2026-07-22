# ModuleType

标识模块类型。

**起始版本：** 9

<!--Device-bundleManager-export enum ModuleType--><!--Device-bundleManager-export enum ModuleType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## ENTRY

```TypeScript
ENTRY = 1
```

应用的主模块，作为应用的入口，提供了应用的基础功能。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ModuleType-ENTRY = 1--><!--Device-ModuleType-ENTRY = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## FEATURE

```TypeScript
FEATURE = 2
```

应用的动态特性模块，作为应用能力的扩展，可以根据用户的需求和设备类型进行选择性安装。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ModuleType-FEATURE = 2--><!--Device-ModuleType-FEATURE = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## SHARED

```TypeScript
SHARED = 3
```

应用的[动态共享库](../../../quick-start/in-app-hsp.md)模块。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ModuleType-SHARED = 3--><!--Device-ModuleType-SHARED = 3-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

