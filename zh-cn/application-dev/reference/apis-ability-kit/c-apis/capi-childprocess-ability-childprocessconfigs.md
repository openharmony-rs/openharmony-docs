# Ability_ChildProcessConfigs

```c
typedef struct Ability_ChildProcessConfigs Ability_ChildProcessConfigs
```

## 概述

启动子进程的配置信息，包括子进程的进程名、数据沙箱与网络环境的共享模式、主进程与子进程的uid是否隔离的配置。开发者可以使用 {@link OH_Ability_ChildProcessConfigs_SetProcessName}、{@link OH_Ability_ChildProcessConfigs_SetIsolationMode}、<br>{@link OH_Ability_ChildProcessConfigs_SetIsolationUid}接口来修改相应的配置信息。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 20

**相关模块：** [ChildProcess](capi-childprocess.md)

**所在头文件：** [native_child_process.h](capi-native-child-process-h.md)

