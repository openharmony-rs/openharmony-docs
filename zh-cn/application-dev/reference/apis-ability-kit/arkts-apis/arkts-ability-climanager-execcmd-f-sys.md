# execCmd（系统接口）

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## execCmd

```TypeScript
function execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise<CliSessionInfo>
```

执行Shell命令，返回会话信息。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.EXEC_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cmd | string | 是 | 要执行的Shell命令。 |
| execCmdOptions | [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i-sys.md) | 否 | 执行命令的可选参数。默认值：详见[ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i-sys.md)的具体属性默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i-sys.md)&gt; | Promise对象。返回会话信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [35600031](../errorcode-ability.md#35600031-工具并发数已达上限) | Maximum number of processes has been reached. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
