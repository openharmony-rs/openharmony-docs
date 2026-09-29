# unregisterCliHook（系统接口）

## 导入模块

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## unregisterCliHook

```TypeScript
function unregisterCliHook(hook: CliHook): Promise<void>
```

取消注册之前注册的CLI Hook。Hook对象必须与传递给registerCliHook的对象相同。若未注册Hook，调用将失败并抛出错误。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.REGISTER_AGENT_HOOK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cliManager-function unregisterCliHook(hook: CliHook): Promise<void>--><!--Device-cliManager-function unregisterCliHook(hook: CliHook): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hook | [CliHook](arkts-ability-clihook-i-sys.md) | 是 | 待取消注册的Hook对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.REGISTER_AGENT_HOOK". |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. Interface caller is not a system app. |
| 35600036 | No hook is registered; nothing to unregister. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
