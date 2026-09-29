# AgentSkill

```TypeScript
export interface AgentSkill
```

Represents a distinct capability or function that an agent can perform.

@typedef AgentSkill

**Since:** 24

<!--Device-unnamed-export interface AgentSkill--><!--Device-unnamed-export interface AgentSkill-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## description

```TypeScript
description: string
```

A detailed description of the skill.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-description: string--><!--Device-AgentSkill-description: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## examples

```TypeScript
examples?: Array<string>
```

Example prompts or scenarios that this skill can handle.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-examples?: Array<string>--><!--Device-AgentSkill-examples?: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

Extension configuration items for the skill.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-extension?: string--><!--Device-AgentSkill-extension?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## id

```TypeScript
id: string
```

A unique identifier for the Skill.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-id: string--><!--Device-AgentSkill-id: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## inputModes

```TypeScript
inputModes?: Array<string>
```

The set of supported input media types for this skill, overriding the agent's defaults.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-inputModes?: Array<string>--><!--Device-AgentSkill-inputModes?: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## name

```TypeScript
name: string
```

A human-readable name.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-name: string--><!--Device-AgentSkill-name: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## outputModes

```TypeScript
outputModes?: Array<string>
```

The set of supported output media types for this skill, overriding the agent's defaults.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-outputModes?: Array<string>--><!--Device-AgentSkill-outputModes?: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## tags

```TypeScript
tags: Array<string>
```

A set of keywords describing the skill's capabilities.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AgentSkill-tags: Array<string>--><!--Device-AgentSkill-tags: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
