# ChildProcessInformation

```TypeScript
export interface ChildProcessInformation
```

The module defines the child process information. The information can be obtained through [getChildProcessInfos](arkts-ability-childprocessmanager-getchildprocessinfos-f.md) of childProcessManager and [getUIAbilityChildProcessInfos](arkts-ability-applicationcontext-c.md#getuiabilitychildprocessinfos) of ApplicationContext.

**Since:** 26.0.1

<!--Device-unnamed-export interface ChildProcessInformation--><!--Device-unnamed-export interface ChildProcessInformation-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parentPid

```TypeScript
parentPid: number
```

PID of the parent process of the child process.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChildProcessInformation-parentPid: int--><!--Device-ChildProcessInformation-parentPid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

PID of the child process.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChildProcessInformation-pid: int--><!--Device-ChildProcessInformation-pid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

Process name of the child process.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChildProcessInformation-processName: string--><!--Device-ChildProcessInformation-processName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
