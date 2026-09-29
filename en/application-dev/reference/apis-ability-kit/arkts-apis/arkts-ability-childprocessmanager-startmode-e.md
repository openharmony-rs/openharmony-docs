# StartMode

```TypeScript
export const enum StartMode
```

Enumerates the child process start modes.

**Since:** 11

<!--Device-childProcessManager-export const enum StartMode--><!--Device-childProcessManager-export const enum StartMode-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SELF_FORK

```TypeScript
SELF_FORK = 0
```

The child process is forked from the application process. The child process started in this mode inherits the resources of the parent process and cannot use Binder IPC to communicate with other processes. Otherwise, the child process will crash.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartMode-SELF_FORK = 0--><!--Device-StartMode-SELF_FORK = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## APP_SPAWN_FORK

```TypeScript
APP_SPAWN_FORK = 1
```

The child process is forked from AppSpawn. The child process started in this mode does not inherit the resources of the parent process and can use Binder IPC to communicate with other processes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartMode-APP_SPAWN_FORK = 1--><!--Device-StartMode-APP_SPAWN_FORK = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
