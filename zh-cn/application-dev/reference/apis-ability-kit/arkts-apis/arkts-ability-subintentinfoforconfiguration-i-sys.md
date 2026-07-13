# SubIntentInfoForConfiguration（系统接口）

用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)的特有信息。

**起始版本：** 23

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## entities

```TypeScript
readonly entities?: Record<string, Object>
```

表示意图包含的实体信息。

**类型：** Record<string, Object>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## form

```TypeScript
readonly form?: FormIntentInfo
```

表示意图绑定的卡片信息。

**类型：** FormIntentInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## inputParams

```TypeScript
readonly inputParams?: Array<Record<string, Object>>
```

表示意图参数的数据格式声明，用于意图调用时定义入参的数据格式。

**类型：** Array<Record<string, Object>>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## outputParams

```TypeScript
readonly outputParams?: Array<Record<string, Object>>
```

表示意图调用返回结果的数据格式声明，用于定义意图调用返回结果的数据格式。

**类型：** Array<Record<string, Object>>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## serviceExtension

```TypeScript
readonly serviceExtension?: ServiceExtensionIntentInfo
```

表示意图绑定的ServiceExtensionAbility组件信息。

**类型：** ServiceExtensionIntentInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## srcEntry

```TypeScript
readonly srcEntry: string
```

表示意图执行文件的相对路径，取值为长度不超过127字节的字符串。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uiAbility

```TypeScript
readonly uiAbility?: UIAbilityIntentInfo
```

表示意图绑定的UIAbility组件信息，包含"ability"字段和"executeMode"字段。

**类型：** UIAbilityIntentInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uiExtension

```TypeScript
readonly uiExtension?: UIExtensionIntentInfo
```

表示意图绑定的UIExtensionAbility组件信息。

**类型：** UIExtensionIntentInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

