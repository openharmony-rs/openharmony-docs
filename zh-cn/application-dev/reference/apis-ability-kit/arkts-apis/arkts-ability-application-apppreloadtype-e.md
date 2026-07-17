# AppPreloadType

表示应用当前进程的预加载类型枚举。

**起始版本：** 22

<!--Device-application-export enum AppPreloadType--><!--Device-application-export enum AppPreloadType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

未发生预加载或预加载数据已被清除。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppPreloadType-UNSPECIFIED = 0--><!--Device-AppPreloadType-UNSPECIFIED = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_PROCESS

```TypeScript
TYPE_CREATE_PROCESS = 1
```

进程最终预加载到进程创建完成阶段。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppPreloadType-TYPE_CREATE_PROCESS = 1--><!--Device-AppPreloadType-TYPE_CREATE_PROCESS = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_ABILITY_STAGE

```TypeScript
TYPE_CREATE_ABILITY_STAGE = 2
```

进程最终预加载到[AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md)创建完成阶段。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppPreloadType-TYPE_CREATE_ABILITY_STAGE = 2--><!--Device-AppPreloadType-TYPE_CREATE_ABILITY_STAGE = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_WINDOW_STAGE

```TypeScript
TYPE_CREATE_WINDOW_STAGE = 3
```

进程最终预加载到[WindowStage](../../apis-arkui/arkts-apis/arkts-window.md)创建完成阶段。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppPreloadType-TYPE_CREATE_WINDOW_STAGE = 3--><!--Device-AppPreloadType-TYPE_CREATE_WINDOW_STAGE = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## TYPE_CREATE_BACKGROUND_ABILITY

```TypeScript
TYPE_CREATE_BACKGROUND_ABILITY = 4
```

进程最终预加载到[onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground-1)执行完成阶段。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppPreloadType-TYPE_CREATE_BACKGROUND_ABILITY = 4--><!--Device-AppPreloadType-TYPE_CREATE_BACKGROUND_ABILITY = 4-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

