# execCmd

## 导入模块

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## execCmd

```TypeScript
function execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise<CliSessionInfo>
```

执行Shell命令，返回会话信息。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** 
- API版本26：ohos.permission.EXEC_CLI_TOOL
- API版本26+：ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cmd | string | 是 | 要执行的Shell命令。 |
| execCmdOptions | [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md) | 否 | 执行命令的可选参数。默认值：详见[ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md)的具体属性默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i.md)&gt; | Promise对象。返回会话信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application.<br>**适用版本：** 26.0.0 |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities.<br>**适用版本：** 26.0.1+ |
| [35600031](../errorcode-ability.md#35600031-工具并发数已达上限) | Maximum number of processes has been reached. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
