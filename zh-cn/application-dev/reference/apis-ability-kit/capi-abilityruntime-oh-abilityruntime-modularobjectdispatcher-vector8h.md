# OH_AbilityRuntime_ModularObjectDispatcher_Vector*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_Vector* OH_AbilityRuntime_ModObjDispatcher_VectorHandle
```

## 概述

向量句柄。

该句柄指向一个动态大小的有序元素集合，所有元素类型相同，支持添加元素、按索引获取元素、查询向量大小和清空操作。

可通过[OH_AbilityRuntime_ModObjDispatcher_VectorCreate](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_vectorcreate)创建，使用完毕后需通过[OH_AbilityRuntime_ModObjDispatcher_VectorRelease](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_vectorrelease)释放。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

