# InvokeOptions (System API)

```TypeScript
interface InvokeOptions
```

Optional parameters for Function invocation. Contains the application context information for the Function invocation.

**Since:** 26.0.0

<!--Device-functionManager-interface InvokeOptions--><!--Device-functionManager-interface InvokeOptions-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## context

```TypeScript
context?: Context
```

Context of the caller.<br>Note: Currently, only [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) is supported.

**Type:** [Context](arkts-ability-context-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InvokeOptions-context?: Context--><!--Device-InvokeOptions-context?: Context-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## dmSessionId

```TypeScript
dmSessionId?: string
```

Indicates the session ID of the dialog manager (DM), which uniquely identifies the agent session. The value consists of letters, digits, '_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-InvokeOptions-dmSessionId?: string--><!--Device-InvokeOptions-dmSessionId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## toolCallId

```TypeScript
toolCallId?: string
```

Indicates the unique identifier assigned to a tool call by the agent. The value consists of letters, digits, '_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-InvokeOptions-toolCallId?: string--><!--Device-InvokeOptions-toolCallId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
