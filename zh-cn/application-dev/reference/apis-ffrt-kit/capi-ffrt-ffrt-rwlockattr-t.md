# ffrt_rwlockattr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} ffrt_rwlockattr_t
```

## 概述

读写锁属性结构体，用于存储读写锁的属性信息。

**起始版本：** 18

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| long storage | 读写锁属性的内部存储。请勿直接访问，直接访问可能导致读写锁属性失效。 |


