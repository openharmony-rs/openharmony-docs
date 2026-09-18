# ffrt_mutex_t

```c
typedef struct ffrt_mutex_t {...} ffrt_mutex_t
```

## 概述

互斥锁结构体，用于存储互斥锁的内部数据。

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [uint32_t storage[(ffrt_mutex_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]](#sizeof) | 互斥锁的内部存储。请勿直接访问，通过`ffrt_mutex_*`等接口管理。 |

## 成员函数说明

### sizeof()

```c
uint32_t storage[(ffrt_mutex_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]
```

**描述：**

互斥锁的内部存储。请勿直接访问，通过`ffrt_mutex_*`等接口管理。


