# ExecResultWrap（系统接口）

```TypeScript
export interface ExecResultWrap
```

onAfterCallTool和onAfterCallCmd的结果参数。

**起始版本：** 26.0.1

<!--Device-unnamed-export interface ExecResultWrap--><!--Device-unnamed-export interface ExecResultWrap-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## dmSessionId

```TypeScript
dmSessionId?: string
```

表示对话管理（DM）会话标识，从[ExecOptions](arkts-ability-climanager-execoptions-i-sys.md)或[ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md)回传。仅当调用方传入该标识时存在。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResultWrap-dmSessionId?: string--><!--Device-ExecResultWrap-dmSessionId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## execResult

```TypeScript
execResult: ExecResult
```

执行结果。

**类型：** [ExecResult](../../apis-ability-kit/arkts-apis/arkts-ability-app-cli-climanager.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResultWrap-execResult: ExecResult--><!--Device-ExecResultWrap-execResult: ExecResult-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## toolCallId

```TypeScript
toolCallId?: string
```

表示工具调用的唯一标识，从[ExecOptions](arkts-ability-climanager-execoptions-i-sys.md)或[ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md)回传。仅当调用方传入该标识时存在。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResultWrap-toolCallId?: string--><!--Device-ExecResultWrap-toolCallId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
