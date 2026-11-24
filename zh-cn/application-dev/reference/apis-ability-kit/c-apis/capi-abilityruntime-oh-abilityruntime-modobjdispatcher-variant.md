# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## 概述

定义使用联合体加类型标签的变体结构，通过类型标签区分实际数据类型，用于在参数传递和返回值接收中安全传递多种类型的值。<br>变体值由vt字段决定实际存储的数据类型和联合体中有效的成员。<br>当变体持有堆分配资源（ 如字符串、容器句柄）时，需调用[OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear)释放。<br>简单类型（布尔、整数、浮点数）不持有堆资源， 无需调用VariantClear释放。

<!--Device-typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant--><!--Device-typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-ability-kit-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ValueType](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype) vt | 变体类型标签，决定联合体中有效的成员。<br>**起始版本：** 26.0.0<br><!--Device-OH_AbilityRuntime_ModObjDispatcher_ValueType vt--><!--Device-OH_AbilityRuntime_ModObjDispatcher_ValueType vt-End--> |
| uint64_t reserved1 | 保留字段1。预留空间供后续版本扩展使用，调用方应将其初始化为0，且不应读取或修改。<br>**起始版本：** 26.0.0<br><!--Device-uint64_t reserved1--><!--Device-uint64_t reserved1-End--> |
| uint64_t reserved2 | 保留字段2。预留空间供后续版本扩展使用，调用方应将其初始化为0，且不应读取或修改。<br>**起始版本：** 26.0.0<br><!--Device-uint64_t reserved2--><!--Device-uint64_t reserved2-End--> |
| uint64_t reserved3 | 保留字段3。预留空间供后续版本扩展使用，调用方应将其初始化为0，且不应读取或修改。<br>**起始版本：** 26.0.0<br><!--Device-uint64_t reserved3--><!--Device-uint64_t reserved3-End--> |
| u.pvoidVal | 空值句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.pvoidVal--><!--Device-u.pvoidVal-End--> |
| u.boolVal | 布尔值。<br>**起始版本：** 26.0.0<br><!--Device-u.boolVal--><!--Device-u.boolVal-End--> |
| u.i8Val | 8位有符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.i8Val--><!--Device-u.i8Val-End--> |
| u.i16Val | 16位有符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.i16Val--><!--Device-u.i16Val-End--> |
| u.i32Val | 32位有符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.i32Val--><!--Device-u.i32Val-End--> |
| u.i64Val | 64位有符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.i64Val--><!--Device-u.i64Val-End--> |
| u.u8Val | 8位无符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.u8Val--><!--Device-u.u8Val-End--> |
| u.u16Val | 16位无符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.u16Val--><!--Device-u.u16Val-End--> |
| u.u32Val | 32位无符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.u32Val--><!--Device-u.u32Val-End--> |
| u.u64Val | 64位无符号整数。<br>**起始版本：** 26.0.0<br><!--Device-u.u64Val--><!--Device-u.u64Val-End--> |
| u.f32Val | 32位浮点数（单精度）。<br>**起始版本：** 26.0.0<br><!--Device-u.f32Val--><!--Device-u.f32Val-End--> |
| u.f64Val | 64位浮点数（双精度）。<br>**起始版本：** 26.0.0<br><!--Device-u.f64Val--><!--Device-u.f64Val-End--> |
| u.enumVal | 枚举值，以int32_t形式存储。<br>**起始版本：** 26.0.0<br><!--Device-u.enumVal--><!--Device-u.enumVal-End--> |
| u.bstrVal | UTF-8字符串句柄，指向堆分配的字符串。<br>**起始版本：** 26.0.0<br><!--Device-u.bstrVal--><!--Device-u.bstrVal-End--> |
| u.parrayVal | 数组句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.parrayVal--><!--Device-u.parrayVal-End--> |
| u.pvectorVal | 向量句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.pvectorVal--><!--Device-u.pvectorVal-End--> |
| u.psetVal | 集合句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.psetVal--><!--Device-u.psetVal-End--> |
| u.pmapVal | 映射句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.pmapVal--><!--Device-u.pmapVal-End--> |
| u.pstructVal | 结构体句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.pstructVal--><!--Device-u.pstructVal-End--> |
| u.premoteProxyVal | 远端Proxy对象句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.premoteProxyVal--><!--Device-u.premoteProxyVal-End--> |
| u.premoteStubVal | 远端Stub对象句柄。<br>**起始版本：** 26.0.0<br><!--Device-u.premoteStubVal--><!--Device-u.premoteStubVal-End--> |


