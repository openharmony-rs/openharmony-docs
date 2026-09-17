# ToolInfo (System API)

ToolInfo describes the basic information of a cli tool.

@typedef ToolInfo

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## description

```TypeScript
readonly description: string
```

The description of the CLI tool.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## eventSchemas

```TypeScript
readonly eventSchemas?: Record<string, Record<string, Object>>
```

Schemas about custom event.

**Type:** Record&lt;string, Record&lt;string, Object&gt;&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## eventTypes

```TypeScript
readonly eventTypes?: Array<string>
```

Supported event types for custom event.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## executablePath

```TypeScript
readonly executablePath: string
```

The executable path of the CLI tool.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## hasSubCommand

```TypeScript
readonly hasSubCommand?: boolean
```

Whether this tool has subcommand.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## inputSchema

```TypeScript
readonly inputSchema: Record<string, Object>
```

The input schema of the CLI tool.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## isLockScreenExecutionAllowed

```TypeScript
readonly isLockScreenExecutionAllowed?: boolean
```

Whether the tool can be executed when the screen is locked.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

The name of the CLI tool.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## outputSchema

```TypeScript
readonly outputSchema: Record<string, Object>
```

The output schema of the CLI tool.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## requirePermissions

```TypeScript
readonly requirePermissions?: Array<string>
```

The require permissions of the CLI tool.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## subcommands

```TypeScript
readonly subcommands?: Record<string, SubCommandInfo>
```

SubCommandInfo list.

**Type:** Record&lt;string, [SubCommandInfo](arkts-ability-toolinfo-subcommandinfo-i-sys.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## version

```TypeScript
readonly version: string
```

The version of the CLI tool (format defined by provider, e.g., "1.0.0").

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
