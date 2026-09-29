# AgentCard

```TypeScript
export interface AgentCard
```

AgentCard describes the basic information and capabilities provided by an Agent.

@typedef AgentCard

**Since:** 24

<!--Device-unnamed-export interface AgentCard--><!--Device-unnamed-export interface AgentCard-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## agentId

```TypeScript
agentId: string
```

A unique identifier for the agent card.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-agentId: string--><!--Device-AgentCard-agentId: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## appInfo

```TypeScript
appInfo: AgentAppInfo
```

Application-related information for the agent.

**Type:** [AgentAppInfo](arkts-ability-agentcard-agentappinfo-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-appInfo: AgentAppInfo--><!--Device-AgentCard-appInfo: AgentAppInfo-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## capabilities

```TypeScript
capabilities?: AgentCapabilities
```

Capability set supported by the agent.

**Type:** [AgentCapabilities](arkts-ability-agentcard-agentcapabilities-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-capabilities?: AgentCapabilities--><!--Device-AgentCard-capabilities?: AgentCapabilities-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## category

```TypeScript
category: string
```

The category of this agent.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-category: string--><!--Device-AgentCard-category: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## defaultInputModes

```TypeScript
defaultInputModes: Array<string>
```

The set of interaction modes that the agent supports across all skills. This can be overridden per skill. Defined as media types.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-defaultInputModes: Array<string>--><!--Device-AgentCard-defaultInputModes: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## defaultOutputModes

```TypeScript
defaultOutputModes: Array<string>
```

The media types supported as outputs from this agent.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-defaultOutputModes: Array<string>--><!--Device-AgentCard-defaultOutputModes: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## description

```TypeScript
description: string
```

The description of the Agent's function.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-description: string--><!--Device-AgentCard-description: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## documentationUrl

```TypeScript
documentationUrl?: string
```

Url for the Agent's documentation.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-documentationUrl?: string--><!--Device-AgentCard-documentationUrl?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

Extension configuration items for the agent.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-extension?: string--><!--Device-AgentCard-extension?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## iconUrl

```TypeScript
iconUrl: string
```

A url to an icon for the agent.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-iconUrl: string--><!--Device-AgentCard-iconUrl: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## name

```TypeScript
name: string
```

The name of the Agent.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-name: string--><!--Device-AgentCard-name: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## provider

```TypeScript
provider?: AgentProvider
```

Service provider information for the Agent.

**Type:** [AgentProvider](arkts-ability-agentcard-agentprovider-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-provider?: AgentProvider--><!--Device-AgentCard-provider?: AgentProvider-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## skills

```TypeScript
skills: Array<AgentSkill>
```

Skills represent the abilities of an agent.

**Type:** Array&lt;[AgentSkill](arkts-ability-agentcard-agentskill-i.md)&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-skills: Array<AgentSkill>--><!--Device-AgentCard-skills: Array<AgentSkill>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## type

```TypeScript
type?: agentConstant.AgentCardType
```

The type of the AgentCard. When `type` is `agentConstant.AgentCardType.LOW_CODE`, the corresponding application must be a system application. Otherwise, the agent card cannot be registered, installed, or updated.

**Type:** [agentConstant.AgentCardType](arkts-ability-agentconstant-agentcardtype-e.md)

**Default:** AgentCardType.APP

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AgentCard-type?: agentConstant.AgentCardType--><!--Device-AgentCard-type?: agentConstant.AgentCardType-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## version

```TypeScript
version: string
```

Version of the Agent (format defined by provider, e.g., "1.0.0").

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentCard-version: string--><!--Device-AgentCard-version: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
