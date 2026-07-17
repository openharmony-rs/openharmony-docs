# LaunchParam

启动参数，主要包括Ability启动原因以及上次退出原因。Ability启动时由系统自动传入，开发者无需修改。

**起始版本：** 9

<!--Device-AbilityConstant-export interface LaunchParam--><!--Device-AbilityConstant-export interface LaunchParam-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { AbilityConstant } from '@kit.AbilityKit';
```

## lastExitDetailInfo

```TypeScript
lastExitDetailInfo?: LastExitDetailInfo
```

表示Ability上次退出时的关键运行信息（含进程ID、退出时间戳、RSS内存值等）。

**类型：** LastExitDetailInfo

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-lastExitDetailInfo?: LastExitDetailInfo--><!--Device-LaunchParam-lastExitDetailInfo?: LastExitDetailInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## lastExitMessage

```TypeScript
lastExitMessage: string
```

表示Ability上次退出的详细原因。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-lastExitMessage: string--><!--Device-LaunchParam-lastExitMessage: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## lastExitReason

```TypeScript
lastExitReason: LastExitReason
```

枚举类型，表示Ability上次退出原因。

**类型：** LastExitReason

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-lastExitReason: LastExitReason--><!--Device-LaunchParam-lastExitReason: LastExitReason-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## launchReason

```TypeScript
launchReason: LaunchReason
```

枚举类型，表示Ability启动原因（如故障恢复拉起、意图调用拉起、原子化服务分享拉起等），详见[LaunchReason](arkts-ability-abilityconstant-launchreason-e.md)。

**类型：** LaunchReason

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-launchReason: LaunchReason--><!--Device-LaunchParam-launchReason: LaunchReason-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## launchReasonMessage

```TypeScript
launchReasonMessage?: string
```

表示Ability启动的详细原因。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-launchReasonMessage?: string--><!--Device-LaunchParam-launchReasonMessage?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## launchUTCTime

```TypeScript
launchUTCTime?: number
```

表示UIAbility开始启动的UTC时间戳，单位为毫秒。

**约束：**

该功能仅在启动UIAbility时生效。对于其他类型的Ability（例如UIExtensionAbility），所获取的启动时间为默认值0。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-launchUTCTime?: long--><!--Device-LaunchParam-launchUTCTime?: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## launchUptime

```TypeScript
launchUptime?: number
```

表示UIAbility开始启动时系统已运行的时间（自系统开机启动以来的时间），单位为毫秒。

**约束：**

该功能仅在启动UIAbility时生效。对于其他类型的Ability（例如UIExtensionAbility），所获取的启动时间为默认值0。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchParam-launchUptime?: long--><!--Device-LaunchParam-launchUptime?: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

