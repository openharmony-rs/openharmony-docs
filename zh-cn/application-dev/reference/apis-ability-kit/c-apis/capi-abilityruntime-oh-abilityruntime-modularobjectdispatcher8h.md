# OH_AbilityRuntime_ModularObjectDispatcher*

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher* OH_AbilityRuntime_ModObjDispatcherHandle
```

## 概述

ModularObject分发器的句柄。<br>该句柄指向一个ModularObject分发器实例，可通过 {@link OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance}或<br>{@link OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance}创建，使用完毕后需通过<br>{@link OH_AbilityRuntime_ModObjDispatcher_Release}释放。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

