# ShellCmdResult

```TypeScript
export interface ShellCmdResult
```

The **ShellCmdResult** module provides the shell command execution result.

> **NOTE:** 
> 
> The APIs of this module can be used only in [JsUnit](../../../application-test/unittest-guidelines.md).

**Since:** 8

<!--Device-unnamed-export interface ShellCmdResult--><!--Device-unnamed-export interface ShellCmdResult-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## exitCode

```TypeScript
exitCode: number
```

Result code of the shell command.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShellCmdResult-exitCode: int--><!--Device-ShellCmdResult-exitCode: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## stdResult

```TypeScript
stdResult: string
```

Standard output of the shell command.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShellCmdResult-stdResult: string--><!--Device-ShellCmdResult-stdResult: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
