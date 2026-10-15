# OH_AbilityRuntime_ModObjDispatcher_TypeInfo

```c
struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...}
```

## 概述

定义参数或返回值的类型信息。<br>使用带标签的联合体u描述类型信息，通过vt字段决定联合体中哪个成员有效。<br>使用完毕后需调用 [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear)释放内部持有的堆资源。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | 类型标签，决定联合体中哪个成员有效。<br>**起始版本：** 26.0.0 |
| u.mapType.keyType | 映射的键类型，仅支持基本类型（BOOL、有符号整数、无符号整数、浮点数、STRING、ENUM）， 不支持容器类型（ARRAY、VECTOR、SET、MAP）和复杂类型（STRUCT、IPC_REMOTE_PROXY、IPC_REMOTE_STUB）。<br>**起始版本：** 26.0.0 |
| u.mapType->pValueType | 值类型描述符的句柄，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0 |
| u.arrayType->pElementType | 元素类型描述符的句柄，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0 |
| u.arrayType.size | 数组的固定大小。<br>**起始版本：** 26.0.0 |
| u->pElementType | 元素类型描述符的句柄，当vt为VECTOR或SET时使用，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0 |
| u.idlType | IDL类型名称字符串，当vt为STRUCT、IPC_REMOTE_PROXY、IPC_REMOTE_STUB、ENUM时使用，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0 |


