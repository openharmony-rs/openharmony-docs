# registerFunctionHook（系统接口）

## 导入模块

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## registerFunctionHook

```TypeScript
function registerFunctionHook(hook: FunctionHook): Promise<void>
```

注册Function Hook，用于拦截Function调用。同一时间只能注册一个Function Hook；若已存在已注册的Hook，再次注册将失败。本接口仅在开发者模式下可用。如需更新已注册的Hook，请先调用unregisterFunctionHook取消注册，再重新注册。Hook对象必须实现FunctionHook中至少一个可选方法。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.REGISTER_AGENT_HOOK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-functionManager-function registerFunctionHook(hook: FunctionHook): Promise<void>--><!--Device-functionManager-function registerFunctionHook(hook: FunctionHook): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hook | [FunctionHook](arkts-ability-functionhook-i-sys.md) | 是 | 实现FunctionHook接口的Hook对象。该对象必须实现至少一个可选方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.REGISTER_AGENT_HOOK". |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. Interface caller is not a system app. |
| 35600034 | The device is not in developer mode. |
| 35600035 | A hook is already registered; unregister it first. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
