# OH_AbilityRuntime_ModularObjectDispatcher_Array*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_Array* OH_AbilityRuntime_ModObjDispatcher_ArrayHandle
```

## 概述

数组句柄。

该句柄指向一个固定大小的有序元素集合，所有元素类型相同，支持按索引设置获取元素和查询数组大小。

可通过[OH_AbilityRuntime_ModObjDispatcher_ArrayCreate](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_arraycreate)创建，使用完毕后需通过[OH_AbilityRuntime_ModObjDispatcher_ArrayRelease](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_arrayrelease)释放。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

