# StateType

保存应用数据场景原因，该类型为枚举。配合UIAbility的[onSaveState()](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate-1)方法使用，可以实现[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。

**起始版本：** 9

<!--Device-AbilityConstant-export enum StateType--><!--Device-AbilityConstant-export enum StateType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION

```TypeScript
CONTINUATION = 0
```

应用迁移场景。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-StateType-CONTINUATION = 0--><!--Device-StateType-CONTINUATION = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## APP_RECOVERY

```TypeScript
APP_RECOVERY = 1
```

应用故障恢复场景。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-StateType-APP_RECOVERY = 1--><!--Device-StateType-APP_RECOVERY = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

