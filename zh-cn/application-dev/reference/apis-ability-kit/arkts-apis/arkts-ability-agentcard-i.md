# AgentCard

AgentCard相当于Agent(智能体)的"名片"，用于描述Agent的能力和技能，由开发者在Agent的配置文件agent_config.json中配置。 一个Agent就是一个AgentExtensionAbility实例。开发者可以通过AgentExtensionContext中的agentCard属性获取到当前AgentExtensionAbility的AgentCard。

**起始版本：** 24

<!--Device-unnamed-export interface AgentCard--><!--Device-unnamed-export interface AgentCard-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## agentId

```TypeScript
agentId: string
```

Agent的唯一标识符，在同一个应用中，agentId不可重复。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-agentId: string--><!--Device-AgentCard-agentId: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## appInfo

```TypeScript
appInfo: AgentAppInfo
```

Agent所在的应用信息。包含Agent所属的应用包名、模块名和能力名等标识信息，用于定位和管理AgentExtensionAbility实例。

**类型：** [AgentAppInfo](arkts-ability-agentcard-agentappinfo-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-appInfo: AgentAppInfo--><!--Device-AgentCard-appInfo: AgentAppInfo-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## capabilities

```TypeScript
capabilities?: AgentCapabilities
```

Agent支持的可选能力集合。定义Agent支持的其他可选能力，如流式响应、推送通知、状态历史查询等。不配置时不启用额外能力。

**类型：** [AgentCapabilities](arkts-ability-agentcard-agentcapabilities-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-capabilities?: AgentCapabilities--><!--Device-AgentCard-capabilities?: AgentCapabilities-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## category

```TypeScript
category: string
```

Agent的类别。用于对Agent进行分类管理，常见的类别包括："productivity"（生产力）、"entertainment"（娱乐）、"education"（教育）、"finance"（金融）、"health"（健康） 等。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-category: string--><!--Device-AgentCard-category: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## defaultInputModes

```TypeScript
defaultInputModes: Array<string>
```

Agent在所有[AgentSkill](arkts-ability-agentcard-agentskill-i.md)上支持的输入模式集。使用MIME类型格式定义支持的输入媒体类型，例如["text/plain"]表示纯文本输入，["application/json"]表 示JSON结构化数据输入，["image/png"]表示图片输入。[AgentSkill](arkts-ability-agentcard-agentskill-i.md)级别的inputModes会覆盖此默认设置。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-defaultInputModes: Array<string>--><!--Device-AgentCard-defaultInputModes: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## defaultOutputModes

```TypeScript
defaultOutputModes: Array<string>
```

Agent在所有[AgentSkill](arkts-ability-agentcard-agentskill-i.md)上支持的输出模式集。使用MIME类型格式定义支持的输出媒体类型，例如["text/plain"]表示纯文本输出，["application/html"]表 示HTML格式输出，["application/json"]表示JSON数据输出。[AgentSkill](arkts-ability-agentcard-agentskill-i.md)级别的outputModes会覆盖此默认设置。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-defaultOutputModes: Array<string>--><!--Device-AgentCard-defaultOutputModes: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## description

```TypeScript
description: string
```

说明Agent的核心功能、用途和适用场景，例如"帮助用户搜索食谱、规划菜单并提供烹饪建议"。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-description: string--><!--Device-AgentCard-description: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## documentationUrl

```TypeScript
documentationUrl?: string
```

Agent文档的URL。提供详细的Agent使用文档、API说明、示例和最佳实践指南，帮助开发者更好地集成和使用该Agent。不配置时不提供文档链接。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-documentationUrl?: string--><!--Device-AgentCard-documentationUrl?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

Agent的扩展配置项。用于存储自定义的扩展配置信息，如Agent开场白、版本协议号等，格式为JSON字符串。不配置时不使用扩展配置。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-extension?: string--><!--Device-AgentCard-extension?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## iconUrl

```TypeScript
iconUrl: string
```

Agent图标的URL。提供Agent的可视化标识图标，用于在UI界面中展示，增强Agent的辨识度和用户体验。 **说明：**系统不校验该字段内容，使用方需自行验证iconUrl的合法性和安全性。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-iconUrl: string--><!--Device-AgentCard-iconUrl: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## name

```TypeScript
name: string
```

Agent的名称。一般用于在UI界面中展示给用户，例如"Recipe Assistant"（食谱助手）。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-name: string--><!--Device-AgentCard-name: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## provider

```TypeScript
provider?: AgentProvider
```

Agent的服务提供商信息，包含提供商的组织名称和官方网站URL，用于标识Agent的来源和版权信息。不配置时不包含提供商信息。

**类型：** [AgentProvider](arkts-ability-agentcard-agentprovider-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-provider?: AgentProvider--><!--Device-AgentCard-provider?: AgentProvider-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## skills

```TypeScript
skills: Array<AgentSkill>
```

Agent提供的功能集合。描述Agent可以执行的特定功能或技能，每个技能定义了具体的用途、标签和使用示例。Agent必须至少包含一个技能。

**类型：** Array&lt;[AgentSkill](arkts-ability-agentcard-agentskill-i.md)&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-skills: Array<AgentSkill>--><!--Device-AgentCard-skills: Array<AgentSkill>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## type

```TypeScript
type?: agentConstant.AgentCardType
```

AgentCard的类型。<!--Del-->当 [agentConstant.AgentCardType](arkts-ability-agentconstant-agentcardtype-e.md) 的枚举值为LOW_CODE时，对应的应用必须是系统应用，否则Agent卡片无法注册、安装或更新。<!--DelEnd-->如果未指定，默认为APP类型。

**类型：** agentConstant.AgentCardType

**默认值：** AgentCardType.APP

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-type?: agentConstant.AgentCardType--><!--Device-AgentCard-type?: agentConstant.AgentCardType-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## version

```TypeScript
version: string
```

Agent的版本号。遵循语义化版本规范（如"1.0.0"），格式由提供商定义。版本号用于标识Agent的功能迭代和兼容性变化。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCard-version: string--><!--Device-AgentCard-version: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

