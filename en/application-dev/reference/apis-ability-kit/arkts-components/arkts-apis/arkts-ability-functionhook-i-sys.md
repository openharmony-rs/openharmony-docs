# FunctionHook (System API)

```TypeScript
export interface FunctionHook
```

Hook interface for intercepting function invocation.

The hook object may implement any subset of the optional methods. Only implemented methods are invoked; unimplemented methods are skipped.

**Since:** 26.0.1

<!--Device-unnamed-export interface FunctionHook--><!--Device-unnamed-export interface FunctionHook-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## onAfterInvokeFunction

```TypeScript
onAfterInvokeFunction?(param: FunctionResultWrap): FunctionResultWrap
```

Called after a function is invoked. The returned object replaces the original result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FunctionHook-onAfterInvokeFunction?(param: FunctionResultWrap): FunctionResultWrap--><!--Device-FunctionHook-onAfterInvokeFunction?(param: FunctionResultWrap): FunctionResultWrap-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [FunctionResultWrap](arkts-ability-functionhook-functionresultwrap-i-sys.md) | Yes | The invocation result parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [FunctionResultWrap](arkts-ability-functionhook-functionresultwrap-i-sys.md) | The (possibly modified) result parameter. |

## onBeforeInvokeFunction

```TypeScript
onBeforeInvokeFunction?(param: InvokeFunctionParam): InvokeFunctionParam
```

Called before a function is invoked. The returned object replaces the original arguments.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FunctionHook-onBeforeInvokeFunction?(param: InvokeFunctionParam): InvokeFunctionParam--><!--Device-FunctionHook-onBeforeInvokeFunction?(param: InvokeFunctionParam): InvokeFunctionParam-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [InvokeFunctionParam](arkts-ability-functionhook-invokefunctionparam-i-sys.md) | Yes | The function invocation parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [InvokeFunctionParam](arkts-ability-functionhook-invokefunctionparam-i-sys.md) | The (possibly modified) parameter. |
