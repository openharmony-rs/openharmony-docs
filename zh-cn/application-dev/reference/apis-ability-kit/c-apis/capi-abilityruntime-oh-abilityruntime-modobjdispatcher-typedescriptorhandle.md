# OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle

```c
struct OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle
```

## 概述

定义ModularObject分发器的类型描述符句柄。<br>该句柄指向类型库元数据的访问接口，可用于查询远端服务定义的接口、方法、枚举和结构体等信息。<br>可通过 {@link OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor}获取，使用完毕后需通过<br>{@link OH_AbilityRuntime_TypeDescriptor_Release}释放。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0 /
typedef struct OH_AbilityRuntime_ModularObjectDispatcher_TypeDescriptor

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

