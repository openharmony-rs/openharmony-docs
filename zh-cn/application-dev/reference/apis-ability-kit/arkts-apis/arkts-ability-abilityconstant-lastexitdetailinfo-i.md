# LastExitDetailInfo

记录Ability所在进程上次退出时的关键运行信息。

**起始版本：** 18

<!--Device-AbilityConstant-export interface LastExitDetailInfo--><!--Device-AbilityConstant-export interface LastExitDetailInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { AbilityConstant } from '@kit.AbilityKit';
```

## exitMsg

```TypeScript
exitMsg: string
```

Ability上次退出时所在进程被kill的描述信息。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-exitMsg: string--><!--Device-LastExitDetailInfo-exitMsg: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## exitSubReason

```TypeScript
exitSubReason: number
```

Ability上次退出的子原因。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-exitSubReason: int--><!--Device-LastExitDetailInfo-exitSubReason: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## killReason

```TypeScript
killReason?: string
```

Ability上次退出时的原因，取值详见[应用终止事件reason字段说明](../../../../dfx/hiappevent-watcher-app-killed-events.md#reason字段说明)。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-killReason?: string--><!--Device-LastExitDetailInfo-killReason?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

Ability上次退出所在进程的进程号。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-pid: int--><!--Device-LastExitDetailInfo-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

Ability上次退出所在进程的名称。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-processName: string--><!--Device-LastExitDetailInfo-processName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processState

```TypeScript
processState?: appManager.ProcessState
```

Ability上次退出时的进程状态。

**类型：** appManager.ProcessState

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-processState?: appManager.ProcessState--><!--Device-LastExitDetailInfo-processState?: appManager.ProcessState-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pss

```TypeScript
pss: number
```

Ability上次退出时所在进程实际使用的物理内存大小，单位KB。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-pss: int--><!--Device-LastExitDetailInfo-pss: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## rss

```TypeScript
rss: number
```

Ability上次退出时所在进程实际占用内存大小，单位KB。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-rss: int--><!--Device-LastExitDetailInfo-rss: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## timestamp

```TypeScript
timestamp: number
```

Ability上次退出时的时间戳。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-timestamp: long--><!--Device-LastExitDetailInfo-timestamp: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

Ability上次退出所在应用的UID。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitDetailInfo-uid: int--><!--Device-LastExitDetailInfo-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

