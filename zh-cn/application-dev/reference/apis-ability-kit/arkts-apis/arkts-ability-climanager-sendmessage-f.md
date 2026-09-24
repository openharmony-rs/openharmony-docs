# sendMessage

## 导入模块

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## sendMessage

```TypeScript
function sendMessage(sessionId: string, message: string): Promise<void>
```

向指定CLI工具会话对应的进程发送消息。

> **说明：** 
> 
> 会话仅限创建进程管理：只有调用`execTool`创建该会话的进程可以调用本接口。其他进程即使获取到`sessionId`，调用本接口也会抛出错误码201（Permission denied）。

**起始版本：** 26.0.1

**需要权限：** 
- API版本26：ohos.permission.EXEC_CLI_TOOL
- API版本26+：ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 目标CLI工具进程的会话ID。 |
| message | string | 是 | 要发送的消息，最大长度为10240字符。超过最大长度时抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application.<br>**适用版本：** 26.0.0 |
| [35600032](../errorcode-ability.md#35600032-指定的session不存在) | The specified session does not exist. |
| [35600033](../errorcode-ability.md#35600033-向工具进程写入消息失败) | Failed to write message to the tool process. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
