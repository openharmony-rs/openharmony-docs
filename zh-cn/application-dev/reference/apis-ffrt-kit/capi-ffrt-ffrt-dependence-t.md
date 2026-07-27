# ffrt_dependence_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} ffrt_dependence_t
```

## 概述

依赖数据项结构，用于描述任务间的单个依赖关系。

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [ffrt_dependence_type_t](capi-type-def-h.md#ffrt_dependence_type_t) type | 依赖类型。 |
| const void* ptr | 依赖指针。数据依赖时指向数据，任务依赖时指向任务句柄。 |


