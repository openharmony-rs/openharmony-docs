# AgentSkill

Represents a distinct capability or function that an agent can perform.

@typedef AgentSkill

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## description

```TypeScript
description: string
```

A detailed description of the skill.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## examples

```TypeScript
examples?: Array<string>
```

Example prompts or scenarios that this skill can handle.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

Extension configuration items for the skill.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## id

```TypeScript
id: string
```

A unique identifier for the Skill.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## inputModes

```TypeScript
inputModes?: Array<string>
```

The set of supported input media types for this skill, overriding the agent's defaults.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## name

```TypeScript
name: string
```

A human-readable name.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## outputModes

```TypeScript
outputModes?: Array<string>
```

The set of supported output media types for this skill, overriding the agent's defaults.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## tags

```TypeScript
tags: Array<string>
```

A set of keywords describing the skill's capabilities.

**Type:** Array&lt;string&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core
