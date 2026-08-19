# execTool（系统接口）

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## execTool

```TypeScript
function execTool(toolName: string, subCommand: string, args: Record<string, Object>, challenge: string,
    execOptions?: ExecOptions): Promise<CliSessionInfo>
```

执行CLI命令

**起始版本：** 26.0.0

**需要权限：** ohos.permission.EXEC_CLI_TOOL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cliManager-function execTool(toolName: string, subCommand: string, args: Record<string, Object>, challenge: string,    execOptions?: ExecOptions): Promise<CliSessionInfo>--><!--Device-cliManager-function execTool(toolName: string, subCommand: string, args: Record<string, Object>, challenge: string,    execOptions?: ExecOptions): Promise<CliSessionInfo>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toolName | string | 是 | 目标工具的名称 |
| subCommand | string | 是 | 此执行操作的子命令 |
| args | Record&lt;string, Object&gt; | 是 | 工具的输入参数 |
| challenge | string | 是 | 从访问令牌管理器获取的唯一标识符 |
| execOptions | [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) | 否 | 此操作的选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i-sys.md)&gt; | 执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35600031](../errorcode-ability.md#35600031-工具并发数已达上限) | Maximum number of processes has been reached. |
| [35600030](../errorcode-ability.md#35600030-cli工具不存在) | No tool with the specified name exists. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission "ohos.permission.EXEC_CLI_TOOL". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system app. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2. The system service failed to communicate with the dependent module. |

