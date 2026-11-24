# OH_AbilityRuntime_ModObjDispatcher_TypeInfo

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...} OH_AbilityRuntime_ModObjDispatcher_TypeInfo
```

## 概述

定义参数或返回值的类型信息。<br>使用带标签的联合体u描述类型信息，通过vt字段决定联合体中哪个成员有效。<br>使用完毕后需调用 [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear)释放内部持有的堆资源。

<!--Device-struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...}--><!--Device-struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...}-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-ability-kit-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ValueType](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype) vt | 类型标签，决定联合体中哪个成员有效。<br>**起始版本：** 26.0.0<br><!--Device-OH_AbilityRuntime_ModObjDispatcher_ValueType vt--><!--Device-OH_AbilityRuntime_ModObjDispatcher_ValueType vt-End--> |
| u.mapType.keyType | 映射的键类型，仅支持基本类型（BOOL、有符号整数、无符号整数、浮点数、STRING、ENUM）， 不支持容器类型（ARRAY、VECTOR、SET、MAP）和复杂类型（STRUCT、IPC_REMOTE_PROXY、IPC_REMOTE_STUB）。<br>**起始版本：** 26.0.0<br><!--Device-u.mapType.keyType--><!--Device-u.mapType.keyType-End--> |
| u.mapType.pValueType | 值类型描述符的句柄，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0<br><!--Device-u.mapType.pValueType--><!--Device-u.mapType.pValueType-End--> |
| u.arrayType.pElementType | 元素类型描述符的句柄，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0<br><!--Device-u.arrayType.pElementType--><!--Device-u.arrayType.pElementType-End--> |
| u.arrayType.size | 数组的固定大小。<br>**起始版本：** 26.0.0<br><!--Device-u.arrayType.size--><!--Device-u.arrayType.size-End--> |
| u.pElementType | 元素类型描述符的句柄，当vt为VECTOR或SET时使用，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0<br><!--Device-u.pElementType--><!--Device-u.pElementType-End--> |
| u.idlType | IDL类型名称字符串，当vt为STRUCT、IPC_REMOTE_PROXY、IPC_REMOTE_STUB、ENUM时使用，需通过TypeInfoClear释放。<br>**起始版本：** 26.0.0<br><!--Device-u.idlType--><!--Device-u.idlType-End--> |


