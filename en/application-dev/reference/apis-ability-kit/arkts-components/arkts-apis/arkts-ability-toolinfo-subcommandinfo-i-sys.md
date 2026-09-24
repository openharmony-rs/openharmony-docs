# SubCommandInfo (System API)

```TypeScript
export interface SubCommandInfo
```

Describes the information of a CLI tool subcommand.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## description

```TypeScript
readonly description: string
```

Description of the subcommand. It should clearly explain the specific function and usage scenario of the subcommand.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## eventSchemas

```TypeScript
readonly eventSchemas?: Record<string, Record<string, Object>>
```

Schema definitions for subcommand custom events. Stored as key-value pairs, where the key is the event type and the value is the JSON Schema definition of the event. The default value is an empty object.

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

## inputSchema

```TypeScript
readonly inputSchema: Record<string, Object>
```

Input schema definition of the subcommand. It uses JSON Schema format to define the structure and type of input parameters.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## outputSchema

```TypeScript
readonly outputSchema: Record<string, Object>
```

Output schema definition of the subcommand. It uses JSON Schema format to define the structure and type of output data.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## requirePermissions

```TypeScript
readonly requirePermissions?: Array<string>
```

List of permissions required by the subcommand. All permission items must be unique strings. The system verifies whether the caller has the required permissions when executing the subcommand, and cannot execute without the corresponding permissions. The default value is an empty array.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
