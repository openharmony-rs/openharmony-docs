# OH_AbilityRuntime_ModularObjectDispatcher*

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

```c
typedef struct OH_AbilityRuntime_ModularObjectDispatcher* OH_AbilityRuntime_ModObjDispatcherHandle
```

## 概述

ModularObject分发器的句柄。

该句柄指向一个ModularObject分发器实例，可通过[OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_createmainserviceinstance)或[OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_createsubinstance)创建，使用完毕后需通过[OH_AbilityRuntime_ModObjDispatcher_Release](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_release)释放。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

