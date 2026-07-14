# IntentResult

意图执行的返回结果，支持[泛型类型](../../../../quick-start/introduction-to-arkts.md#泛型类和接口)。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## code

```TypeScript
code: number
```

意图执行返回的错误码，由开发者定义。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: T
```

意图执行返回的结果，通常会包含需要返回给系统入口的数据。

**类型：** T

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

