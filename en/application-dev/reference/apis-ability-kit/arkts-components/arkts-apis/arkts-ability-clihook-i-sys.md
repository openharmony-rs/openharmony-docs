# CliHook (System API)

```TypeScript
export interface CliHook
```

Hook interface for intercepting CLI tool and command execution.

The hook object may implement any subset of the optional methods. Only implemented methods are invoked; unimplemented methods are skipped.

**Since:** 26.0.1

<!--Device-unnamed-export interface CliHook--><!--Device-unnamed-export interface CliHook-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## onAfterCallCmd

```TypeScript
onAfterCallCmd?(param: ExecResultWrap): ExecResultWrap
```

Called after a command is executed. The returned object replaces the original result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliHook-onAfterCallCmd?(param: ExecResultWrap): ExecResultWrap--><!--Device-CliHook-onAfterCallCmd?(param: ExecResultWrap): ExecResultWrap-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | Yes | The execution result parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | The (possibly modified) result parameter. |

## onAfterCallTool

```TypeScript
onAfterCallTool?(param: ExecResultWrap): ExecResultWrap
```

Called after a tool is executed. The returned object replaces the original result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliHook-onAfterCallTool?(param: ExecResultWrap): ExecResultWrap--><!--Device-CliHook-onAfterCallTool?(param: ExecResultWrap): ExecResultWrap-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | Yes | The execution result parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [ExecResultWrap](arkts-ability-clihook-execresultwrap-i-sys.md) | The (possibly modified) result parameter. |

## onBeforeCallCmd

```TypeScript
onBeforeCallCmd?(param: ExecCmdParam): ExecCmdParam
```

Called before a command is executed. The returned object replaces the original parameter.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliHook-onBeforeCallCmd?(param: ExecCmdParam): ExecCmdParam--><!--Device-CliHook-onBeforeCallCmd?(param: ExecCmdParam): ExecCmdParam-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [ExecCmdParam](arkts-ability-clihook-execcmdparam-i-sys.md) | Yes | The original command execution parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [ExecCmdParam](arkts-ability-clihook-execcmdparam-i-sys.md) | The (possibly modified) parameter. |

## onBeforeCallTool

```TypeScript
onBeforeCallTool?(param: ExecToolParam): ExecToolParam
```

Called before a tool is executed. The returned object replaces the original parameter.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliHook-onBeforeCallTool?(param: ExecToolParam): ExecToolParam--><!--Device-CliHook-onBeforeCallTool?(param: ExecToolParam): ExecToolParam-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [ExecToolParam](arkts-ability-clihook-exectoolparam-i-sys.md) | Yes | The original tool execution parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [ExecToolParam](arkts-ability-clihook-exectoolparam-i-sys.md) | The (possibly modified) parameter. |
