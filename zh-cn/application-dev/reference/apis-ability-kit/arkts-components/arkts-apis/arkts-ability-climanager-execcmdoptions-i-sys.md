# ExecCmdOptions

```TypeScript
interface ExecCmdOptions
```

执行Shell命令的可选参数。可用于指定工作目录、环境变量、后台运行、前台执行时长、超时时长、安全策略及事件回调。

**起始版本：** 26.0.1

<!--Device-cliManager-interface ExecCmdOptions--><!--Device-cliManager-interface ExecCmdOptions-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## 导入模块

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## challenge

```TypeScript
challenge?: string
```

从访问令牌管理器获取的唯一标识符。

默认值：""。

**类型：** string

**默认值：** ""

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-challenge?: string--><!--Device-ExecCmdOptions-challenge?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## dmSessionId

```TypeScript
dmSessionId?: string
```

对话管理（DM）会话标识，唯一标识一次Agent会话。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-dmSessionId?: string--><!--Device-ExecCmdOptions-dmSessionId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## isShellCommand

```TypeScript
isShellCommand?: boolean
```

指示命令是否作为shell命令执行。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-isShellCommand?: boolean--><!--Device-ExecCmdOptions-isShellCommand?: boolean-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## toolCallId

```TypeScript
toolCallId?: string
```

工具调用的唯一标识，由Agent分配。取值由字母、数字、'_'和'-'组成，最大长度为256。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-toolCallId?: string--><!--Device-ExecCmdOptions-toolCallId?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
