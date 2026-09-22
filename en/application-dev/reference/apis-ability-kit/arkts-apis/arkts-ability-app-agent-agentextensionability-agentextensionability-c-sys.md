# AgentExtensionAbility

```TypeScript
declare class AgentExtensionAbility extends ExtensionAbility
```

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

Triggered when a [LOW_CODE](../../../reference/apis-ability-kit/js-apis-app-agent-agentConstant-sys.md#agentconstantagentcardtype) agent is successfully invoked, used for initialization operations (such as downloading resources from the cloud and loading configurations).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agentId | string | Yes | Indicates the LOW_CODE agent ID. |
