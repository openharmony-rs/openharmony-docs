# ChildProcessInformation

模块定义子进程信息。这些信息可以通过[getChildProcessInfos](arkts-ability-childprocessmanager-getchildprocessinfos-f.md)的子进程管理器和[getUIAbilityChildProcessInfos](arkts-ability-applicationcontext-c.md#getuiabilitychildprocessinfos)的ApplicationContext。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parentPid

```TypeScript
parentPid: number
```

子进程的父进程PID。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

子进程的PID。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

子进程的进程名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
