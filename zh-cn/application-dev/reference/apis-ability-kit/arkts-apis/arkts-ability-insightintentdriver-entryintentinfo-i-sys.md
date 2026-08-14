# EntryIntentInfo（系统接口）

FormIntentInfo用于描述 @InsightIntentForm 装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)所绑定的卡片信 息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-insightIntentDriver-interface EntryIntentInfo--><!--Device-insightIntentDriver-interface EntryIntentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityName

```TypeScript
readonly abilityName: string
```

Ability名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntryIntentInfo-readonly abilityName: string--><!--Device-EntryIntentInfo-readonly abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## executeMode

```TypeScript
readonly executeMode: insightIntent.ExecuteMode[]
```

意图调用执行模式。即拉起绑定的Ability时支持的执行模式。

**类型：** insightIntent.ExecuteMode[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntryIntentInfo-readonly executeMode: insightIntent.ExecuteMode[]--><!--Device-EntryIntentInfo-readonly executeMode: insightIntent.ExecuteMode[]-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

