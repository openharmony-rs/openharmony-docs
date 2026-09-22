# OH_AbilityRuntime_ModularObjectDispatcher_Array*

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_Array* OH_AbilityRuntime_ModObjDispatcher_ArrayHandle
```

## 概述

数组句柄。<br>该句柄指向一个固定大小的有序元素集合，所有元素类型相同，支持按索引设置获取元素和查询数组大小。<br>可通过 {@link OH_AbilityRuntime_ModObjDispatcher_ArrayCreate}创建，使用完毕后需通过<br>{@link OH_AbilityRuntime_ModObjDispatcher_ArrayRelease}释放。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

