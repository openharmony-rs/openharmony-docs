# AgentExtensionContext

```TypeScript
declare class AgentExtensionContext extends ExtensionContext
```

AgentExtensionContext is the context environment of [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md), inheriting from [ExtensionContext](arkts-ability-extensioncontext-c.md).

AgentExtensionContext provides developers with the capability to access the [AgentCard](arkts-ability-agentcard-i.md) information configured by the current [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md) agent.

> **NOTE:** 
> 
> - In the examples in this document, `this.context` is used to obtain the `AgentExtensionContext`, where `this`represents an instance inheriting from `AgentExtensionAbility`.

@extends ExtensionContext

**Inheritance/Implementation:** AgentExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## agentCard

```TypeScript
agentCard: AgentCard
```

The [AgentCard](arkts-ability-agentcard-i.md) information configured by the current [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md) agent, used to describe the basic information and capabilities of the agent.

**Type:** [AgentCard](arkts-ability-agentcard-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core
