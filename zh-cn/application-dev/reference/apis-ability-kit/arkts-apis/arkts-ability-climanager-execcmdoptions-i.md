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

## background

```TypeScript
background?: boolean
```

表示命令是否后台执行。

true：后台执行，false：前台执行。

默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## callback

```TypeScript
callback?: ToolEventCallback
```

事件回调函数，用于接收工具事件。若提供该参数，将自动订阅会话事件。

**类型：** [ToolEventCallback](arkts-ability-tooleventcallback-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## env

```TypeScript
env?: Record<string, string>
```

命令执行的环境变量。

**类型：** Record&lt;string, string&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## policy

```TypeScript
policy?: string
```

安全策略，参数格式为JSON字符串。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## timeout

```TypeScript
timeout?: number
```

命令执行超时时长，单位为秒。取值范围：0 ~ 1800。默认值：1800，传0表示不会超时。

**类型：** number

**默认值：** 1800

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## workDir

```TypeScript
workDir?: string
```

命令执行的工作目录，如果不传或传空，则为根目录。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## yieldMs

```TypeScript
yieldMs?: number
```

命令前台执行时长，单位为毫秒。取值范围：0 ~ 1000 * timeout，默认值：0。

**类型：** number

**默认值：** 0

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
