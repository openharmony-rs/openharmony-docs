# PrepareTermination

应用准备关闭时返回的动作，该类型为枚举。需要配合[AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md)的[onPrepareTermination](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onpreparetermination-1)或者[onPrepareTerminationAsync](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onprepareterminationasync-1)方法使用。

**起始版本：** 15

<!--Device-AbilityConstant-export enum PrepareTermination--><!--Device-AbilityConstant-export enum PrepareTermination-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## TERMINATE_IMMEDIATELY

```TypeScript
TERMINATE_IMMEDIATELY = 0
```

表示立即执行结束动作，默认值。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PrepareTermination-TERMINATE_IMMEDIATELY = 0--><!--Device-PrepareTermination-TERMINATE_IMMEDIATELY = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL

```TypeScript
CANCEL = 1
```

表示取消结束动作。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PrepareTermination-CANCEL = 1--><!--Device-PrepareTermination-CANCEL = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

