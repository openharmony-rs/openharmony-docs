# Ability_ChildProcessConfigs

```c
typedef struct Ability_ChildProcessConfigs Ability_ChildProcessConfigs
```

## Overview

Configuration information for starting a child process, including the process name of the child process, the isolation mode (used to configure whether the data sandbox and network environment are shared or isolated), and whether the UID of the main process and the child process are isolated. Developers can use [OH_Ability_ChildProcessConfigs_SetProcessName](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setprocessname), [OH_Ability_ChildProcessConfigs_SetIsolationMode](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setisolationmode), and [OH_Ability_ChildProcessConfigs_SetIsolationUid](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setisolationuid) to modify the corresponding configuration information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 20

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

