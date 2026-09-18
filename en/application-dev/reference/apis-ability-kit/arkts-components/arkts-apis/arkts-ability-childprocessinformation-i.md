# ChildProcessInformation

The module defines the child process information. The information can be obtained through [getChildProcessInfos](arkts-ability-childprocessmanager-getchildprocessinfos-f.md) of childProcessManager and [getUIAbilityChildProcessInfos](arkts-ability-applicationcontext-c.md#getuiabilitychildprocessinfos) of ApplicationContext.

**Since:** 26.1.0

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parentPid

```TypeScript
parentPid: number
```

PID of the parent process of the child process.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

PID of the child process.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

Process name of the child process.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
