# FunctionHook（系统接口）

```TypeScript
export interface FunctionHook
```

用于拦截Function调用的Hook接口。

Hook对象可实现可选方法的任意子集。仅已实现的方法会被调用；未实现的方法将被跳过。

**起始版本：** 26.0.1

<!--Device-unnamed-export interface FunctionHook--><!--Device-unnamed-export interface FunctionHook-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## onAfterInvokeFunction

```TypeScript
onAfterInvokeFunction?(param: FunctionResultWrap): FunctionResultWrap
```

Function调用后调用。返回的对象将替换原始结果。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FunctionHook-onAfterInvokeFunction?(param: FunctionResultWrap): FunctionResultWrap--><!--Device-FunctionHook-onAfterInvokeFunction?(param: FunctionResultWrap): FunctionResultWrap-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [FunctionResultWrap](arkts-ability-functionhook-functionresultwrap-i-sys.md) | 是 | 调用结果参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FunctionResultWrap](arkts-ability-functionhook-functionresultwrap-i-sys.md) | 返回（可能已被修改的）结果参数。 |

## onBeforeInvokeFunction

```TypeScript
onBeforeInvokeFunction?(param: InvokeFunctionParam): InvokeFunctionParam
```

Function调用前调用。返回的对象将替换原始参数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FunctionHook-onBeforeInvokeFunction?(param: InvokeFunctionParam): InvokeFunctionParam--><!--Device-FunctionHook-onBeforeInvokeFunction?(param: InvokeFunctionParam): InvokeFunctionParam-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [InvokeFunctionParam](arkts-ability-functionhook-invokefunctionparam-i-sys.md) | 是 | Function调用参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InvokeFunctionParam](arkts-ability-functionhook-invokefunctionparam-i-sys.md) | 返回（可能已被修改的）参数。 |
