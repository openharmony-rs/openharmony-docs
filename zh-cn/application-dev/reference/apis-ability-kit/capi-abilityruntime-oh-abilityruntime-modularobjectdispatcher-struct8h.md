# OH_AbilityRuntime_ModularObjectDispatcher_Struct*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_Struct* OH_AbilityRuntime_ModObjDispatcher_StructHandle
```

## 概述

结构体句柄。

该句柄指向一个具名字段的结构体实例，字段类型通过类型库元数据定义。

可通过[OH_AbilityRuntime_ModObjDispatcher_StructCreate](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_structcreate)创建，使用完毕后需通过[OH_AbilityRuntime_ModObjDispatcher_StructRelease](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_structrelease)释放。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

