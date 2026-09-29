# InvokeOptions（系统接口）

```TypeScript
interface InvokeOptions
```

Function调用的可选参数。包含Function调用时的应用上下文信息。

**起始版本：** 26.0.0

<!--Device-functionManager-interface InvokeOptions--><!--Device-functionManager-interface InvokeOptions-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## context

```TypeScript
context?: Context
```

执行Function调用时的应用上下文信息。<br>说明：目前仅支持[UIAbilityContext](arkts-ability-uiabilitycontext-c.md)。

**类型：** [Context](arkts-ability-context-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeOptions-context?: Context--><!--Device-InvokeOptions-context?: Context-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## dmSessionId

```TypeScript
dmSessionId?: string
```

对话管理（DM）会话标识，唯一标识一次Agent会话。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeOptions-dmSessionId?: string--><!--Device-InvokeOptions-dmSessionId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## toolCallId

```TypeScript
toolCallId?: string
```

工具调用的唯一标识，由Agent分配。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeOptions-toolCallId?: string--><!--Device-InvokeOptions-toolCallId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
