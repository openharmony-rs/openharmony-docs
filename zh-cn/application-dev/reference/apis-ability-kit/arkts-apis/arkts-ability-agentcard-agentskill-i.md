# AgentSkill

表示Agent可以执行的不同能力或功能。

**起始版本：** 24

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## description

```TypeScript
description: string
```

AgentSkill的详细描述。应清晰说明该技能的具体功能、适用场景和能解决的问题，例如"帮助用户规划两点之间的出行路线，提供多种交通方式选择和实时路况信息"。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## examples

```TypeScript
examples?: Array<string>
```

AgentSkill可以处理的示例提示或使用场景。提供具体的示例可以帮助用户理解如何使用该技能，例如["规划从上海到北京的路线"]。不配置时不展示示例。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

AgentSkill的扩展配置项。用于存储技能级别的自定义扩展配置，格式为JSON字符串，可以包含技能特有的参数和配置信息。不配置时不使用扩展配置。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## id

```TypeScript
id: string
```

AgentSkill的唯一标识符，在一个AgentCard中必须唯一。建议使用具有语义的命名格式（如"route-planner"、"recipe-search"），用于在API调用中精确指定要使用的技能。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## inputModes

```TypeScript
inputModes?: Array<string>
```

AgentSkill支持的输入模式。使用MIME类型格式定义，例如["text/plain"]。如果未设置，将使用AgentCard级别的defaultInputModes。该字段允许为特定技能自定义输入类型，覆盖默认设置。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## name

```TypeScript
name: string
```

AgentSkill的名称。用于在UI界面中展示，例如"Route Planning"（路线规划）或"Recipe Search"（食谱搜索）。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## outputModes

```TypeScript
outputModes?: Array<string>
```

AgentSkill支持的输出模式。使用MIME类型格式定义，例如["text/plain", "application/html", "video/mp4"]。如果未设置，将使用AgentCard级别的 defaultOutputModes。该字段允许为特定技能自定义输出类型，覆盖默认设置。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## tags

```TypeScript
tags: Array<string>
```

描述AgentSkill能力的关键字标签。用于技能分类、检索和推荐，例如["maps", "routing", "navigation"]或["cooking", "recipe", "food"]。标签应简洁明了，便于用户理解和 搜索。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
