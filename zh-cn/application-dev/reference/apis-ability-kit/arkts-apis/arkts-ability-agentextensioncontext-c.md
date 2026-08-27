# AgentExtensionContext

AgentExtensionContext模块是 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)的上下文环境，继承自 [ExtensionContext](arkts-ability-extensioncontext-c.md)。AgentExtensionContext为开发者提供访问当前 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)智能体所配置的AgentCard信息的能力。

> **说明：**
> 
> - 在本文档的示例中，通过`this.context`来获取`AgentExtensionContext`，其中`this`代表继承自`AgentExtensionAbility`的实例。
@extends ExtensionContext

**继承/实现关系：** AgentExtensionContext extends ExtensionContext

**起始版本：** 24

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## agentCard

```TypeScript
agentCard: AgentCard
```

当前[AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)智能体所配置的 [AgentCard](arkts-ability-agentcard-i.md)信息，用于描述智能体的基本信息和能力。

**类型：** [AgentCard](arkts-ability-agentcard-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
