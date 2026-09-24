# ToolInfo (System API)

```TypeScript
export interface ToolInfo
```

ToolInfo describes the basic information of a CLI tool, including the tool name, version, description, executable path, and input/output schema.

@typedef ToolInfo

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

## eventSchemas

```TypeScript
readonly eventSchemas?: Record<string, Record<string, Object>>
```

Schema definitions for custom events. Stored as key-value pairs, where the key is the event type and the value is the JSON Schema definition of the event. The default value is an empty object.

**Type:** Record&lt;string, Record&lt;string, Object&gt;&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## eventTypes

```TypeScript
readonly eventTypes?: Array<string>
```

List of custom event types supported by the CLI tool. All event types must be unique strings. The default value is an empty array.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## executablePath

```TypeScript
readonly executablePath: string
```

Executable file path of the CLI tool. It must be an absolute path.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## hasSubCommand

```TypeScript
readonly hasSubCommand?: boolean
```

Indicates whether the tool supports subcommands. **true** means the tool supports subcommands, **false** means it does not. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## inputSchema

```TypeScript
readonly inputSchema: Record<string, Object>
```

Input schema definition of the CLI tool. It uses JSON Schema format to define the structure and type of input parameters, used to describe the input data format accepted by the tool.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## isLockScreenExecutionAllowed

```TypeScript
readonly isLockScreenExecutionAllowed?: boolean
```

Indicates whether the tool supports execution in the lock screen state. **true** means the tool supports execution in the lock screen state, **false** means the tool does not support execution in the lock screen state. The default value is **false**.

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

Name of the CLI tool, used to uniquely identify a CLI tool in the system. The maximum length is 32 and cannot be empty.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## outputSchema

```TypeScript
readonly outputSchema: Record<string, Object>
```

Output schema definition of the CLI tool. It uses JSON Schema format to define the structure and type of output data, used to describe the output data format returned by the tool.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## requirePermissions

```TypeScript
readonly requirePermissions?: Array<string>
```

List of permissions required by the CLI tool. All permission items must be unique strings. The system verifies whether the caller has the required permissions when executing the tool, and cannot execute without the corresponding permissions. The default value is an empty array.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## subcommands

```TypeScript
readonly subcommands?: Record<string, SubCommandInfo>
```

List of subcommand information. Stored as key-value pairs, where the key is the subcommand name and the value is the detailed information of the subcommand. The default value is an empty object.

**Type:** Record&lt;string, [SubCommandInfo](arkts-ability-toolinfo-subcommandinfo-i-sys.md)&gt;

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
