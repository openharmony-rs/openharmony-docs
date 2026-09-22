# InvokeFunctionParam (System API)

```TypeScript
export interface InvokeFunctionParam
```

Parameter for function hook interception.

**Since:** 26.0.1

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## args

```TypeScript
args: Record<string, Object>
```

Indicates the original function arguments.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## functionName

```TypeScript
functionName: string
```

Indicates the name of the function.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## functionNamespace

```TypeScript
functionNamespace: string
```

Indicates the namespace of the function.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## invokeOptions

```TypeScript
invokeOptions?: InvokeOptions
```

Indicates the invocation options.

**Type:** [InvokeOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-function-functionmanager.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
