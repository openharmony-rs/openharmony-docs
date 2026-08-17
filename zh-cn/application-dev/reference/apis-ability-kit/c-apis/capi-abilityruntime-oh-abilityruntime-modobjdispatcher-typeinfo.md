# OH_AbilityRuntime_ModObjDispatcher_TypeInfo

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...} OH_AbilityRuntime_ModObjDispatcher_TypeInfo
```

## 概述

定义参数或返回值的类型信息。<br>使用带标签的联合体u描述类型信息，通过vt字段决定联合体中哪个成员有效。<br>使用完毕后需调用[OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear)释放内部持有的堆资源。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | 类型标签，决定联合体中哪个成员有效。<br>**起始版本：** 26.0.0 |
| union | 类型特定的元数据联合体。有效的成员由vt决定。<br>**起始版本：** 26.0.0 |


