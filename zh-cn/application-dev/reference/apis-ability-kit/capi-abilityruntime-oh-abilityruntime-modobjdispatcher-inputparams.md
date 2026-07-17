# OH_AbilityRuntime_ModObjDispatcher_InputParams

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

```c
typedef struct {...} OH_AbilityRuntime_ModObjDispatcher_InputParams
```

## 概述

定义方法调用的参数结构。rgvarg指向参数变体数组，数组长度由cArgs指定。参数顺序应与方法定义中的参数顺序一致。

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

**所在头文件：** [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_Variant*](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md) rgvarg | 参数变体数组。<br>**起始版本：** 26.0.0 |
| uint32_t cArgs | 参数数量。<br>**起始版本：** 26.0.0 |


