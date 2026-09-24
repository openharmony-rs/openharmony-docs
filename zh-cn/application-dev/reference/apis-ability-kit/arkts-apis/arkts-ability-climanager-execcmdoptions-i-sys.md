# ExecCmdOptions

```TypeScript
interface ExecCmdOptions
```

执行Shell命令的可选参数。可用于指定工作目录、环境变量、后台运行、前台执行时长、超时时长、安全策略及事件回调。

**起始版本：** 26.0.1

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

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
