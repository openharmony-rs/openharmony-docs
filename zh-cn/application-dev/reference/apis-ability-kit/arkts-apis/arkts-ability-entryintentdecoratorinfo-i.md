# EntryIntentDecoratorInfo

EntryIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md)，用于描述
[@InsightIntentEntry](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry)
装饰器支持的参数。

**继承/实现关系：** EntryIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

表示与意图绑定的Ability名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## executeMode

```TypeScript
executeMode?: insightIntent.ExecuteMode[]
```

The execute mode of the intent.
For UIAbility, the parameter can be set to insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND or
insightIntent.ExecuteMode.UI_ABILITY_UI_ABILITY_BACKGROUND or both of them.

**类型：** insightIntent.ExecuteMode[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

