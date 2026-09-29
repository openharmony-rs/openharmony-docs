# ffrt_rwlock_t

```c
typedef struct ffrt_rwlock_t {...} ffrt_rwlock_t
```

## 概述

读写锁结构体，用于存储读写锁的内部数据。

**系统能力：** SystemCapability.Resourceschedule.Ffrt.Core

**起始版本：** 18

**相关模块：** [FFRT](capi-ffrt.md)

**所在头文件：** [type_def.h](capi-type-def-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t storage[(ffrt_rwlock_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | 读写锁的内部存储。请勿直接访问，通过`ffrt_rwlock_*`等接口管理。 |


