# invokePublicFunction

## 导入模块

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## invokePublicFunction

```TypeScript
function invokePublicFunction(functionNamespace: string, functionName: string,
    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>
```

根据函数命名空间和函数名称调用公开函数（Function），使用Promise异步回调。三方应用通过ACL授权获取权限后可调用此接口执行公开函数（Function）。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_PUBLIC_FUNCTION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-functionManager-function invokePublicFunction(functionNamespace: string, functionName: string,    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>--><!--Device-functionManager-function invokePublicFunction(functionNamespace: string, functionName: string,    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| functionNamespace | string | 是 | 目标函数的命名空间。 |
| functionName | string | 是 | 目标函数的名称。 |
| args | Record&lt;string, Object&gt; | 是 | 函数的输入参数。 |
| options | [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i.md) | 否 | 函数的调用选项。默认值：详见[InvokeOptions](arkts-ability-functionmanager-invokeoptions-i.md)的具体属性默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[InvokeResult](arkts-ability-functionmanager-invokeresult-i.md)&gt; | Promise对象，返回函数执行结果[InvokeResult](arkts-ability-functionmanager-invokeresult-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
| [35600060](../errorcode-ability.md#35600060-function不存在) | The function does not exist. |
| [35600061](../errorcode-ability.md#35600061-function执行失败) | The function execute failed. |
| [35600062](../errorcode-ability.md#35600062-function执行超时) | The function execute timeout. |
