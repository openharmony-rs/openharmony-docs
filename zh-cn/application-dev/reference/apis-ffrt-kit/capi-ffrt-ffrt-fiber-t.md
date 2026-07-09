# ffrt_fiber_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} ffrt_fiber_t
```

## 概述

纤程结构体，用于存储纤程执行上下文。

**起始版本：** 20

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uintptr_t storage[ffrt_fiber_storage_size] | 纤程执行上下文的内部存储。请勿直接访问，通过{@link ffrt_fiber_init}初始化，通过{@link ffrt_fiber_switch}切换。 |


