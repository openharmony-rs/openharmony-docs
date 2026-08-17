# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## 概述

定义使用联合体加类型标签的变体结构，通过类型标签区分实际数据类型，用于在参数传递和返回值接收中安全传递多种类型的值。<br>变体值由vt字段决定实际存储的数据类型和联合体中有效的成员。<br>当变体持有堆分配资源（如字符串、容器句柄）时，需调用[OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear)释放。<br>简单类型（布尔、整数、浮点数）不持有堆资源，无需调用VariantClear释放。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | 变体类型标签，决定联合体中有效的成员。<br>**起始版本：** 26.0.0 |
| uint64_t reserved1 | 保留字段1。预留空间供后续版本扩展使用，调用方应将其初始化为0，且不应读取或修改。<br>**起始版本：** 26.0.0 |
| uint64_t reserved2 | 保留字段2。预留空间供后续版本扩展使用，调用方应将其初始化为0，且不应读取或修改。<br>**起始版本：** 26.0.0 |
| uint64_t reserved3 | 保留字段3。预留空间供后续版本扩展使用，调用方应将其初始化为0，且不应读取或修改。<br>**起始版本：** 26.0.0 |
| union | 变体值数据联合体。有效的成员由vt决定。<br>**起始版本：** 26.0.0 |


