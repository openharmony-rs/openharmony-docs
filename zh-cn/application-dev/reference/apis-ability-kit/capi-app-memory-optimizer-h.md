# app_memory_optimizer.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

声明用于通知系统子进程活跃状态的应用内存优化接口。

**引用文件：** <AbilityKit/ability_runtime/app_memory_optimizer.h>

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.1.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AbilityRuntime_ChildProcessState](#oh_abilityruntime_childprocessstate) | OH_AbilityRuntime_ChildProcessState | 表示子进程活跃状态的枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_NotifyChildProcessState(int32_t pid, OH_AbilityRuntime_ChildProcessState state)](#oh_abilityruntime_notifychildprocessstate) | 通知系统当前应用子进程的活跃状态。 |

## 枚举类型说明

### OH_AbilityRuntime_ChildProcessState

```c
enum OH_AbilityRuntime_ChildProcessState
```

**描述**

表示子进程活跃状态的枚举。子进程启动时默认处于活跃状态。

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_ACTIVE = 0 | 子进程处于活跃状态，系统不会对其执行内存优化。 |
| OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_INACTIVE = 1 | 子进程处于非活跃状态，系统可以对其执行内存优化。 |

## 函数说明

### OH_AbilityRuntime_NotifyChildProcessState()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_NotifyChildProcessState(int32_t pid, OH_AbilityRuntime_ChildProcessState state)
```

**描述**

通知系统当前应用子进程的活跃状态。

当子进程被标记为非活跃状态时，系统可以对其执行内存优化；当子进程被重新标记为活跃状态时，系统会停止对其执行内存优化。仅支持标记当前应用创建的子进程。

仅支持标记通过系统子进程创建接口创建的子进程。应用自身fork出来的进程（例如直接调用fork()，或通过[childProcessManager.startChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartchildprocess)以SELF_FORK模式启动的进程）不支持标记；通过其他子进程创建接口（例如[childProcessManager.startArkChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartarkchildprocess12)、[childProcessManager.startNativeChildProcess](js-apis-app-ability-childProcessManager.md#childprocessmanagerstartnativechildprocess13)，以及[OH_Ability_StartNativeChildProcess](capi-native-child-process-h.md#oh_ability_startnativechildprocess)等NDK接口）创建的子进程支持标记。

该接口只能在应用的主进程中调用。如果在子进程中调用，返回[ABILITY_RUNTIME_ERROR_CODE_CHILD_PROCESS_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode)。

该接口线程安全，可以在任意线程调用。该调用为同步调用，会阻塞至结果返回。对同一子进程重复通知相同状态具有幂等性：调用仍然成功，且不会触发额外的状态变化回调。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t pid | 子进程的PID，为子进程创建接口返回的PID。 |
| [OH_AbilityRuntime_ChildProcessState](#oh_abilityruntime_childprocessstate) state | 要设置的子进程活跃状态。仅接受OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_ACTIVE和OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_INACTIVE，传入其他值时返回[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 传入的参数无效。<br>ABILITY_RUNTIME_ERROR_CODE_CHILD_PROCESS_NOT_EXIST - 子进程不存在或不是当前应用创建的子进程，或者在子进程中调用了该接口。 |
