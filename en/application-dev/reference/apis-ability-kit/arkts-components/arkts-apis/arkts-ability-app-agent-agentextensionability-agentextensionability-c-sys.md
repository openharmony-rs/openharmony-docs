# AgentExtensionAbility

The class of agent extension ability. This class cannot be used in Harmony Archive(HAR).

@extends ExtensionAbility

**Inheritance/Implementation:** AgentExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { AgentExtensionAbility } from '@kit.AbilityKit';
```

## onAgentInvoked

```TypeScript
onAgentInvoked(agentId: string): void
```

Called back when a LOW_CODE agent is invoked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agentId | string | Yes | Indicates the LOW_CODE agent ID. |
