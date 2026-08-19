# ExecCmdOptions（系统接口）

执行Shell命令的可选参数。可用于指定工作目录、环境变量、后台运行、前台执行时长、超时时长、安全策略及事件回调。

**起始版本：** 26.0.0

<!--Device-cliManager-interface ExecCmdOptions--><!--Device-cliManager-interface ExecCmdOptions-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## background

```TypeScript
background?: boolean
```

表示命令是否后台执行。 true：后台执行，false：前台执行。 默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-background?: boolean--><!--Device-ExecCmdOptions-background?: boolean-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## callback

```TypeScript
callback?: ToolEventCallback
```

事件回调函数，用于接收工具事件。若提供该参数，将自动订阅会话事件。

**类型：** [ToolEventCallback](arkts-ability-tooleventcallback-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-callback?: ToolEventCallback--><!--Device-ExecCmdOptions-callback?: ToolEventCallback-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## env

```TypeScript
env?: Record<string, string>
```

命令执行的环境变量。

**类型：** Record&lt;string, string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-env?: Record<string, string>--><!--Device-ExecCmdOptions-env?: Record<string, string>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## policy

```TypeScript
policy?: string
```

安全策略，参数格式为JSON字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-policy?: string--><!--Device-ExecCmdOptions-policy?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## timeout

```TypeScript
timeout?: long
```

命令执行超时时长，单位为秒。取值范围：0 ~ 1800。默认值：1800，传0表示不会超时。

**类型：** long

**默认值：** 1800

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-timeout?: long--><!--Device-ExecCmdOptions-timeout?: long-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## workDir

```TypeScript
workDir?: string
```

命令执行的工作目录，如果不传或传空，则为根目录。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-workDir?: string--><!--Device-ExecCmdOptions-workDir?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## yieldMs

```TypeScript
yieldMs?: long
```

任务前台执行时长。取值范围：0 ~ 1000 * timeout。默认值：0。单位：ms。

**类型：** long

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecCmdOptions-yieldMs?: long--><!--Device-ExecCmdOptions-yieldMs?: long-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

