# EntryIntentInfo（系统接口）

FormIntentInfo用于描述
[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)
装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的卡片信
息。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityName

```TypeScript
readonly abilityName: string
```

Ability名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## executeMode

```TypeScript
readonly executeMode: insightIntent.ExecuteMode[]
```

意图调用执行模式。即拉起绑定的Ability时支持的执行模式。

**类型：** insightIntent.ExecuteMode[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

