# FunctionResultWrap（系统接口）

```TypeScript
export interface FunctionResultWrap
```

onAfterInvokeFunction的结果参数。

**起始版本：** 26.0.1

<!--Device-unnamed-export interface FunctionResultWrap--><!--Device-unnamed-export interface FunctionResultWrap-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## dmSessionId

```TypeScript
dmSessionId?: string
```

表示对话管理（DM）会话标识，从[InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md)回传。仅当调用方传入该标识时存在。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FunctionResultWrap-dmSessionId?: string--><!--Device-FunctionResultWrap-dmSessionId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result: InvokeResult
```

调用结果。

**类型：** [InvokeResult](../../apis-ability-kit/arkts-apis/arkts-ability-app-function-functionmanager.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FunctionResultWrap-result: InvokeResult--><!--Device-FunctionResultWrap-result: InvokeResult-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## toolCallId

```TypeScript
toolCallId?: string
```

表示Function调用的唯一标识，从[InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md)回传。仅当调用方传入该标识时存在。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FunctionResultWrap-toolCallId?: string--><!--Device-FunctionResultWrap-toolCallId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
