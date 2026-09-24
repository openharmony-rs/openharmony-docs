# FunctionInfo（系统接口）

```TypeScript
export interface FunctionInfo
```

FunctionInfo用于描述[Function](arkts-ability-app-function-functionmanager.md)的基本信息，包括Function命名空间、名称、版本、描述、输入输出模式等。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## description

```TypeScript
readonly description: string
```

Function的功能描述。该描述应清晰说明Function的核心功能和用途，帮助用户和AI Agent理解Function能做什么，用于辅助决策。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## functionName

```TypeScript
readonly functionName: string
```

Function的名称，用于在functionNamespace内唯一标识一个Function。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## functionNamespace

```TypeScript
readonly functionNamespace: string
```

Function的命名空间，用于在系统中对Function进行分类和管理。命名空间可以帮助组织和识别不同功能领域的Function。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## inputSchema

```TypeScript
readonly inputSchema?: string
```

Function的输入参数JSON Schema定义，描述Function接受的输入参数结构和类型。需要符合JSON Schema格式定义。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## outputSchema

```TypeScript
readonly outputSchema?: string
```

Function的输出结果JSON Schema定义，描述Function返回值的结构和类型。需要符合JSON Schema格式定义。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## version

```TypeScript
readonly version: string
```

Function的版本号。遵循语义化版本规范（如"1.0.0"），格式由提供商定义。版本号用于标识Function的功能迭代和兼容性变化。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
