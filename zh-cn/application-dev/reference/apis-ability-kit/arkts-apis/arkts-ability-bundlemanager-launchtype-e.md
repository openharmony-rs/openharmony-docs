# LaunchType

标识组件的[启动模式](../../../application-models/uiability-launch-type.md)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-bundleManager-export enum LaunchType--><!--Device-bundleManager-export enum LaunchType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## SINGLETON

```TypeScript
SINGLETON = 0
```

UIAbility的启动模式，表示单实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchType-SINGLETON = 0--><!--Device-LaunchType-SINGLETON = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## MULTITON

```TypeScript
MULTITON = 1
```

UIAbility的启动模式，表示普通多实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchType-MULTITON = 1--><!--Device-LaunchType-MULTITON = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## SPECIFIED

```TypeScript
SPECIFIED = 2
```

UIAbility的启动模式，表示该UIAbility内部根据业务自己指定多实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchType-SPECIFIED = 2--><!--Device-LaunchType-SPECIFIED = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

