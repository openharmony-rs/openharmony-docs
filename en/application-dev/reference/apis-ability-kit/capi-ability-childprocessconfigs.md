# Ability_ChildProcessConfigs

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=5bb247b05c17392f13f8ef23a0a57c57e37f2a5a translatedAt=2026-11-04T09:46:28.000Z pushedAt=2026-11-04T09:49:23.984Z nl=1 -->

```c
typedef struct Ability_ChildProcessConfigs Ability_ChildProcessConfigs;
```

## Overview

Configuration information for starting a child process, including the process name of the child process, the sharing mode of the data sandbox and network environment, and the configuration of whether the UID of the main process and the child process are isolated. Developers can use [OH_Ability_ChildProcessConfigs_SetProcessName](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setprocessname), [OH_Ability_ChildProcessConfigs_SetIsolationMode](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setisolationmode), and [OH_Ability_ChildProcessConfigs_SetIsolationUid](capi-native-child-process-h.md#oh_ability_childprocessconfigs_setisolationuid) to modify the corresponding configuration information.

**Since**: 20

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)
