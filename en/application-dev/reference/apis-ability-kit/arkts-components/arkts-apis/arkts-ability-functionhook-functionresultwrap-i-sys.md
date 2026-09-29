# FunctionResultWrap (System API)

```TypeScript
export interface FunctionResultWrap
```

Result parameter for onAfterInvokeFunction.

**Since:** 26.0.1

<!--Device-unnamed-export interface FunctionResultWrap--><!--Device-unnamed-export interface FunctionResultWrap-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## dmSessionId

```TypeScript
dmSessionId?: string
```

Indicates the session ID of the dialog manager (DM), echoed from [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md). Present only when the caller passed it. The value consists of letters, digits,'_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FunctionResultWrap-dmSessionId?: string--><!--Device-FunctionResultWrap-dmSessionId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## result

```TypeScript
result: InvokeResult
```

Indicates the invocation result.

**Type:** [InvokeResult](../../apis-ability-kit/arkts-apis/arkts-ability-app-function-functionmanager.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FunctionResultWrap-result: InvokeResult--><!--Device-FunctionResultWrap-result: InvokeResult-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## toolCallId

```TypeScript
toolCallId?: string
```

Indicates the unique identifier of the function call, echoed from [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md). Present only when the caller passed it. The value consists of letters, digits,'_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FunctionResultWrap-toolCallId?: string--><!--Device-FunctionResultWrap-toolCallId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
