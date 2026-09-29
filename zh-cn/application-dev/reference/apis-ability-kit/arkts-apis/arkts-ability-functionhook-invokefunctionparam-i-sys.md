# InvokeFunctionParam（系统接口）

```TypeScript
export interface InvokeFunctionParam
```

Function Hook拦截的参数。

**起始版本：** 26.0.1

<!--Device-unnamed-export interface InvokeFunctionParam--><!--Device-unnamed-export interface InvokeFunctionParam-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## args

```TypeScript
args: Record<string, Object>
```

原始Function参数。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeFunctionParam-args: Record<string, Object>--><!--Device-InvokeFunctionParam-args: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## functionName

```TypeScript
functionName: string
```

Function的名称。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeFunctionParam-functionName: string--><!--Device-InvokeFunctionParam-functionName: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## functionNamespace

```TypeScript
functionNamespace: string
```

Function的命名空间。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeFunctionParam-functionNamespace: string--><!--Device-InvokeFunctionParam-functionNamespace: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## invokeOptions

```TypeScript
invokeOptions?: InvokeOptions
```

调用选项。

**类型：** [InvokeOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-function-functionmanager.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeFunctionParam-invokeOptions?: InvokeOptions--><!--Device-InvokeFunctionParam-invokeOptions?: InvokeOptions-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
