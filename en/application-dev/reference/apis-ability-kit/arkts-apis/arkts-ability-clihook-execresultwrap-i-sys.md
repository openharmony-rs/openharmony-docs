# ExecResultWrap (System API)

```TypeScript
export interface ExecResultWrap
```

Result parameter for onAfterCallTool and onAfterCallCmd.

**Since:** 26.0.1

<!--Device-unnamed-export interface ExecResultWrap--><!--Device-unnamed-export interface ExecResultWrap-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## dmSessionId

```TypeScript
dmSessionId?: string
```

Indicates the session ID of the dialog manager (DM), echoed from [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) or [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md). Present only when the caller passed it. The value consists of letters, digits,'_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResultWrap-dmSessionId?: string--><!--Device-ExecResultWrap-dmSessionId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## execResult

```TypeScript
execResult: ExecResult
```

Indicates the execution result.

**Type:** [ExecResult](../../apis-ability-kit/arkts-apis/arkts-ability-app-cli-climanager.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResultWrap-execResult: ExecResult--><!--Device-ExecResultWrap-execResult: ExecResult-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## toolCallId

```TypeScript
toolCallId?: string
```

Indicates the unique identifier of the tool call, echoed from [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) or [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md). Present only when the caller passed it. The value consists of letters, digits,'_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResultWrap-toolCallId?: string--><!--Device-ExecResultWrap-toolCallId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
