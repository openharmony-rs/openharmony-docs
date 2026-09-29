# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef union OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## 概述

定义使用联合体加类型标签的变体结构，通过类型标签区分实际数据类型，用于在参数传递和返回值接收中安全传递多种类型的值。<br>变体值由vt字段决定实际存储的数据类型和联合体中有效的成员。<br>当变体持有堆分配资源（ 如字符串、容器句柄）时，需调用[OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear)释放。<br>简单类型（布尔、整数、浮点数）不持有堆资源， 无需调用VariantClear释放。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| void *pvoidVal | 空值句柄。<br>**起始版本：** 26.0.0 |
| bool boolVal | 布尔值。<br>**起始版本：** 26.0.0 |
| int8_t i8Val | 8位有符号整数。<br>**起始版本：** 26.0.0 |
| int16_t i16Val | 16位有符号整数。<br>**起始版本：** 26.0.0 |
| int32_t i32Val | 32位有符号整数。<br>**起始版本：** 26.0.0 |
| int64_t i64Val | 64位有符号整数。<br>**起始版本：** 26.0.0 |
| uint8_t u8Val | 8位无符号整数。<br>**起始版本：** 26.0.0 |
| uint16_t u16Val | 16位无符号整数。<br>**起始版本：** 26.0.0 |
| uint32_t u32Val | 32位无符号整数。<br>**起始版本：** 26.0.0 |
| uint64_t u64Val | 64位无符号整数。<br>**起始版本：** 26.0.0 |
| float f32Val | 32位浮点数（单精度）。<br>**起始版本：** 26.0.0 |
| double f64Val | 64位浮点数（双精度）。<br>**起始版本：** 26.0.0 |
| int32_t enumVal | 枚举值，以int32_t形式存储。<br>**起始版本：** 26.0.0 |
| char* bstrVal | UTF-8字符串句柄，指向堆分配的字符串。<br>**起始版本：** 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-arrayhandle.md) parrayVal | 数组句柄。<br>**起始版本：** 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-vectorhandle.md) pvectorVal | 向量句柄。<br>**起始版本：** 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-sethandle.md) psetVal | 集合句柄。<br>**起始版本：** 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-maphandle.md) pmapVal | 映射句柄。<br>**起始版本：** 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-structhandle.md) pstructVal | 结构体句柄。<br>**起始版本：** 26.0.0 |
| OHIPCRemoteProxy *premoteProxyVal | 远端Proxy对象句柄。<br>**起始版本：** 26.0.0 |
| OHIPCRemoteStub *premoteStubVal;
 } u | 远端Stub对象句柄。<br>**起始版本：** 26.0.0 |


