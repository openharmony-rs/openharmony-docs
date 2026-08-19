# sendMessage（系统接口）

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## sendMessage

```TypeScript
function sendMessage(sessionId: string, message: string): Promise<void>
```

向指定CLI工具会话对应的进程发送消息。 > **说明：** > > 会话仅限创建进程管理：只有调用`execTool`创建该会话的进程可以调用本接口。其他进程即使获取到`sessionId`，调用本接口也会抛出错误码201（Permission denied）。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.EXEC_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cliManager-function sendMessage(sessionId: string, message: string): Promise<void>--><!--Device-cliManager-function sendMessage(sessionId: string, message: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

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
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission "ohos.permission.EXEC_CLI_TOOL". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system app. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
| [35600033](../errorcode-ability.md#35600033-向工具进程写入消息失败) | failed to write message to tool. |
| [35600032](../errorcode-ability.md#35600032-指定的session不存在) | The session does not exist. |

