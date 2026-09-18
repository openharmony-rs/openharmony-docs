# ChildProcessArgs

The module describes the parameters transferred to the child process. When starting a child process through [childProcessManager](arkts-ability-app-ability-childprocessmanager.md), you can transfer parameters to the child process through **ChildProcessArgs**.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ChildProcessArgs } from '@kit.AbilityKit';
```

## entryParams

```TypeScript
entryParams?: string
```

Custom parameters to be transparently transmitted to the child process. The parameters can be obtained through **args.entryParams** in [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart). The maximum data volume supported by **entryParams** is 150 KB.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## fds

```TypeScript
fds?: Record<string, number>
```

File Descriptor (FD) handles, which are used for communication between the main process and child process. They are passed to the child process in the form of key-value pairs, where **key** is a custom string and **value** is a DF handle. The FD handles can be obtained through **args.fds** in [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart).

&lt;b&gt;NOTE&lt;/b&gt;

- **fds** supports a maximum of 16 groups. In each group, **key** contains a maximum of 20 characters.  
- The ID of a handle passed to the child process may change, but the handle always points to the same file.

**Type:** Record&lt;string, number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
