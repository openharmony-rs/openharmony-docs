# OH_AbilityRuntime_ModularObjectDispatcher_Map*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_Map* OH_AbilityRuntime_ModObjDispatcher_MapHandle
```

## 概述

映射句柄。

该句柄指向一个键值对的有序集合，键和值类型在创建时指定，支持添加或更新键值对、按键获取值、删除键值对、查询指定键是否存在、按索引获取键或值、查询映射大小和清空操作。

键仅支持基本类型（BOOL、有符号整数、无符号整数、浮点数、STRING、ENUM）。

可通过[OH_AbilityRuntime_ModObjDispatcher_MapCreate](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_mapcreate)创建，使用完毕后需通过[OH_AbilityRuntime_ModObjDispatcher_MapRelease](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_maprelease)释放。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

