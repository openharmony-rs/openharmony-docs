# @ohos.app.cli.cliManager

本模块提供与系统命令行工具（CLI）的交互能力，可以查询工具信息、调用并执行CLI命令，以及管理会话。会话在调用execTool接口时创建，用于跟踪CLI工具的执行状态和结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace cliManager--><!--Device-unnamed-declare namespace cliManager-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearSession](arkts-ability-climanager-clearsession-f-sys.md) | 关闭指定CLI工具会话，并强制结束对应的工具进程。 |
| [execCmd](arkts-ability-climanager-execcmd-f-sys.md) | 执行Shell命令，返回会话信息。使用Promise异步回调。 |
| [execTool](arkts-ability-climanager-exectool-f-sys.md) | 执行CLI命令 |
| [getToolInfoByName](arkts-ability-climanager-gettoolinfobyname-f-sys.md) | 根据工具名称获取单个工具的详细信息，使用Promise异步回调。 |
| [querySession](arkts-ability-climanager-querysession-f-sys.md) | 查询指定CLI工具会话的状态和执行结果。 |
| [queryToolSummaries](arkts-ability-climanager-querytoolsummaries-f-sys.md) | 查询所有CLI工具的摘要信息。摘要信息仅包含名称、版本和描述字段，使用Promise异步回调。 |
| [queryTools](arkts-ability-climanager-querytools-f-sys.md) | 查询所有CLI工具的详细信息，使用Promise异步回调。 |
| [sendMessage](arkts-ability-climanager-sendmessage-f-sys.md) | 向指定CLI工具会话对应的进程发送消息。 |
| [subscribeSession](arkts-ability-climanager-subscribesession-f-sys.md) | 订阅指定CLI工具会话的事件。会话运行期间，CLI工具产生的标准输出、标准错误、退出或错误事件通过回调返回。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CliSessionInfo](arkts-ability-climanager-clisessioninfo-i-sys.md) | 执行CLI工具时，系统会为调用方和CLI工具建立一个会话，此字段描述会话信息的格式。 |
| [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i-sys.md) | 执行Shell命令的可选参数。可用于指定工作目录、环境变量、后台运行、前台执行时长、超时时长、安全策略及事件回调。 |
| [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) | 执行CLI工具的可选参数。可用于指定CLI工具后台运行、前台执行时长、超时时长。 |
| [ExecResult](arkts-ability-climanager-execresult-i-sys.md) | CLI工具执行的结果。包含CLI工具的退出码、标准输出、标准错误输出、终止信号、是否超时及执行时长。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SessionStatus](arkts-ability-climanager-sessionstatus-e-sys.md) | 执行CLI工具时，系统会为调用方和CLI工具建立一个会话，此字段描述会话状态。 |
<!--DelEnd-->

