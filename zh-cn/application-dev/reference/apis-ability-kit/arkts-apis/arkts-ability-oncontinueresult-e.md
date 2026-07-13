# OnContinueResult

Ability迁移结果，该类型为枚举，可配合UIAbility的[onContinue()](arkts-ability-uiability-c.md#oncontinue-1)方法完成相应的返回。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## AGREE

```TypeScript
AGREE = 0
```

表示同意。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REJECT

```TypeScript
REJECT = 1
```

表示拒绝：如应用在[onContinue](arkts-ability-uiability-c.md#oncontinue-1)中异常会导致迁移以后数据恢复时显示异常，则可以返回REJECT。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MISMATCH

```TypeScript
MISMATCH = 2
```

表示版本不匹配：迁移发起端应用可以在[onContinue](arkts-ability-uiability-c.md#oncontinue-1)中获取到迁移目标端应用的版本号，进行协商后，如果版本不
匹配导致无法迁移，可以返回该结果。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

