# ToolSummary (System API)

```TypeScript
export interface ToolSummary
```

Describes the summary information of a CLI tool.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## description

```TypeScript
readonly description: string
```

Functional description of the CLI tool. The description should clearly explain the core function and purpose of the tool, helping users understand what the tool can do.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Name of the CLI tool, used to uniquely identify a CLI tool in the system. The maximum length is 32 and cannot be empty.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## version

```TypeScript
readonly version: string
```

Version number of the CLI tool. It follows semantic versioning (e.g., "1.0.0"), and the format is defined by the provider. The version number is used to identify the tool's feature iteration and compatibility changes.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
