# FunctionInfo (System API)

```TypeScript
export interface FunctionInfo
```

FunctionInfo describes the basic information of a [Function](arkts-ability-app-function-functionmanager.md), including the Function namespace, name, version, description, and input/output schema.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## description

```TypeScript
readonly description: string
```

Functional description of the Function. The description should clearly explain the core function and purpose of the Function, helping users and AI Agents understand what the Function can do, used for assisting in decision-making.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## functionName

```TypeScript
readonly functionName: string
```

Name of the Function, used to uniquely identify a Function within the functionNamespace.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## functionNamespace

```TypeScript
readonly functionNamespace: string
```

Namespace of the Function, used to classify and manage Functions in the system. The namespace helps organize and identify Functions in different functional domains.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## inputSchema

```TypeScript
readonly inputSchema?: string
```

Input parameter JSON Schema definition of the Function, describing the structure and type of input parameters accepted by the Function. It must conform to the JSON Schema format definition.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## outputSchema

```TypeScript
readonly outputSchema?: string
```

Output result JSON Schema definition of the Function, describing the structure and type of the Function return value. It must conform to the JSON Schema format definition.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## version

```TypeScript
readonly version: string
```

Version number of the Function. It follows semantic versioning (e.g., "1.0.0"), and the format is defined by the provider. The version number is used to identify the function iteration and compatibility changes of the Function.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
