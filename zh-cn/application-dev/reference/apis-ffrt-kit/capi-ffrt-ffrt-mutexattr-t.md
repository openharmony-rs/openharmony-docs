# ffrt_mutexattr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} ffrt_mutexattr_t
```

## 概述

互斥锁属性结构体，用于存储互斥锁的属性信息。

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| long storage | 互斥锁属性的内部存储。请勿直接访问，通过[ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init)初始化。 |


