# ChildProcessOptions

The module describes the startup configuration of a child process. When starting a child process through [childProcessManager](arkts-ability-app-ability-childprocessmanager.md), you can configure the startup configuration of the child process through **ChildProcessOptions**.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ChildProcessOptions } from '@kit.AbilityKit';
```

## isolationMode

```TypeScript
isolationMode?: boolean
```

Controls the sandbox isolation level and network access permissions of the child process. **true** if the child process runs in an independent sandbox environment and cannot access the network; **false** if the child process shares the sandbox and network environment with the main process. The default value is **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isolationUid

```TypeScript
isolationUid?: boolean
```

Whether the child process uses an independent UID. **true** if the child process uses an independent UID; **false** if the child process and the main process share the same UID. The default value is **false**. This parameter is valid only when **isolationMode** is set to **true**.

**Type:** boolean

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
