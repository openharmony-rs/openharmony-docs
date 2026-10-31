# Ability_ChildProcessConfigs

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=8e4ee7947dfeb3a89be0dfff4e576f69a510a94f translatedAt=2026-09-03T08:28:27.721Z pushedAt=2026-09-05T10:47:30.046Z -->

```c
typedef struct Ability_ChildProcessConfigs Ability_ChildProcessConfigs;
```

## Overview

Configuration information for starting a child process, including the process name of the child process, the isolation mode (used to configure whether the data sandbox and network environment are shared or isolated), and whether the UID of the main process and the child process are isolated. Developers can use [OH_Ability_ChildProcessConfigs_SetProcessName](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setprocessname), [OH_Ability_ChildProcessConfigs_SetIsolationMode](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setisolationmode), and [OH_Ability_ChildProcessConfigs_SetIsolationUid](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setisolationuid) to modify the corresponding configuration information.

**Since**: 20

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)
