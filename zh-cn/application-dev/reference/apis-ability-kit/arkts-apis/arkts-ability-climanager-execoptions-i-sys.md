# ExecOptions（系统接口）

执行CLI工具的可选参数。可用于指定CLI工具后台运行、前台执行时长、超时时长。

**起始版本：** 26.0.0

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

表示任务是否后台执行。

true：后台执行，false：前台执行。

默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## timeout

```TypeScript
timeout?: number
```

任务执行超时时长。取值范围：0 ~ 1800。默认值：1800。单位：s。

**类型：** number

**默认值：** 1800

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## yieldMs

```TypeScript
yieldMs?: number
```

任务前台执行时长。取值范围：0 ~ 1000 * timeout。默认值：0。单位：ms。

**类型：** number

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
