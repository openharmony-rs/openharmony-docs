# OnSaveResult

保存应用数据的结果，该类型为枚举。配合UIAbility的
[onSaveState()](arkts-ability-uiability-c.md#onsavestate-1)
方法使用，可以实现[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ALL_AGREE

```TypeScript
ALL_AGREE = 0
```

总是同意保存状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION_REJECT

```TypeScript
CONTINUATION_REJECT = 1
```

拒绝迁移保存状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION_MISMATCH

```TypeScript
CONTINUATION_MISMATCH = 2
```

迁移不匹配。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RECOVERY_AGREE

```TypeScript
RECOVERY_AGREE = 3
```

同意恢复保存状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RECOVERY_REJECT

```TypeScript
RECOVERY_REJECT = 4
```

拒绝恢复保存状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ALL_REJECT

```TypeScript
ALL_REJECT = 5
```

Always rejected to save the status.

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

