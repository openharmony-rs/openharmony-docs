# ExecResult（系统接口）

CLI工具执行的结果。包含CLI工具的退出码、标准输出、标准错误输出、终止信号、是否超时及执行时长。

**起始版本：** 26.0.0

<!--Device-cliManager-interface ExecResult--><!--Device-cliManager-interface ExecResult-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## errorText

```TypeScript
errorText?: string
```

工具的标准错误输出（stderr）。默认值：undefined。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResult-errorText?: string--><!--Device-ExecResult-errorText?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## executionTime

```TypeScript
executionTime: long
```

工具的执行时长。单位：ms。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResult-executionTime: long--><!--Device-ExecResult-executionTime: long-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## exitCode

```TypeScript
exitCode?: int
```

工具的退出码。默认值：undefined。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResult-exitCode?: int--><!--Device-ExecResult-exitCode?: int-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## outputText

```TypeScript
outputText?: string
```

工具的标准输出（stdout）。默认值：undefined。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResult-outputText?: string--><!--Device-ExecResult-outputText?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## signalNumber

```TypeScript
signalNumber?: int
```

工具的终止信号。默认值：undefined。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResult-signalNumber?: int--><!--Device-ExecResult-signalNumber?: int-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## timeOut

```TypeScript
timeOut: boolean
```

工具的执行是否超时。true表示超时，false表示未超时。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecResult-timeOut: boolean--><!--Device-ExecResult-timeOut: boolean-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

