# HiDebug_NativeMemInfo

```c
typedef struct HiDebug_NativeMemInfo {...} HiDebug_NativeMemInfo
```

## 概述

Defines the struct for the local memory information of the application process.

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t pss | Proportional set size, in KB. |
| uint32_t vss | Virtual memory size, in KB. |
| uint32_t rss | Resident set size, in KB. |
| uint32_t sharedDirty | Size of the shared dirty memory, in KB. |
| uint32_t privateDirty | Size of the private dirty memory, in KB. |
| uint32_t sharedClean | Size of the shared clean memory, in KB. |
| uint32_t privateClean | Size of the private clean memory, in KB. |


