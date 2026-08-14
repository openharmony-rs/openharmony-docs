# ProcessInformation

运行进程信息，可以通过appManager的 [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getRunningProcessInformation)来获取运行进程信息 。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ProcessInformation--><!--Device-unnamed-export interface ProcessInformation-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## appCloneIndex

```TypeScript
appCloneIndex?: int
```

分身应用索引。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-appCloneIndex?: int--><!--Device-ProcessInformation-appCloneIndex?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleNames

```TypeScript
bundleNames: Array<string>
```

进程中所有运行的Bundle名称。

**类型：** Array&lt;string&gt;

**默认值：** an array of the bundleNames running in the process

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-bundleNames: Array<string>--><!--Device-ProcessInformation-bundleNames: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleType

```TypeScript
bundleType: bundleManager.BundleType
```

当前进程运行的包类型。

**类型：** bundleManager.BundleType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-bundleType: bundleManager.BundleType--><!--Device-ProcessInformation-bundleType: bundleManager.BundleType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isPreload

```TypeScript
isPreload?: boolean
```

进程是否为预加载。当进程是预加载且还未被某个组件启动请求所使用时为true；反之为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-isPreload?: boolean--><!--Device-ProcessInformation-isPreload?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: int
```

进程ID。

**类型：** int

**默认值：** process id

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-pid: int--><!--Device-ProcessInformation-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

进程名称。

**类型：** string

**默认值：** the name of the process

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-processName: string--><!--Device-ProcessInformation-processName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: appManager.ProcessState
```

当前进程运行状态。

**类型：** appManager.ProcessState

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-state: appManager.ProcessState--><!--Device-ProcessInformation-state: appManager.ProcessState-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: int
```

应用程序的UID。

**类型：** int

**默认值：** user id

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProcessInformation-uid: int--><!--Device-ProcessInformation-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

