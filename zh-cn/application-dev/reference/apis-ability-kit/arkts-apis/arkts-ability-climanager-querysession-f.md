# querySession

## 导入模块

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## querySession

```TypeScript
function querySession(sessionId: string): Promise<CliSessionInfo>
```

查询指定CLI工具会话的状态和执行结果。

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

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i.md)&gt; | The info of target session. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 201 | Permission denied. |
| 202 | Not system application.<br>**适用版本：** 26.0.0 |
| 35600032 | The specified session does not exist. |
| 35600050 | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
