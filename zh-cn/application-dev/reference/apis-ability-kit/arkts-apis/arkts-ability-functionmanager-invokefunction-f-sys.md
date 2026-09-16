# invokeFunction（系统接口）

## 导入模块

```TypeScript
import { functionManager } from '@kit.AbilityKit';
```

## invokeFunction

```TypeScript
function invokeFunction(functionNamespace: string, functionName: string,
    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>
```

根据Function命名空间和Function名称调用指定的Function，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_FUNCTION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| functionNamespace | string | 是 | 目标Function的命名空间，与functionName共同确定唯一的Function。 |
| functionName | string | 是 | 目标Function的名称，与functionNamespace共同确定唯一的Function。 |
| args | Record&lt;string, Object&gt; | 是 | 符合Function提供方定义格式的输入参数。 |
| options | [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md) | 否 | Function调用的可选参数。默认值：详见[InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md)的具体属性默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[InvokeResult](arkts-ability-functionmanager-invokeresult-i-sys.md)&gt; | Promise对象。返回Function调用的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
| [35600060](../errorcode-ability.md#35600060-function不存在) | The function does not exist. |
| [35600061](../errorcode-ability.md#35600061-function执行失败) | The function execute failed. |
| [35600062](../errorcode-ability.md#35600062-function执行超时) | The function execute timeout. |
