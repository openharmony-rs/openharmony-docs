# HiDebug_MallocDispatch

```c
typedef struct HiDebug_MallocDispatch {...} HiDebug_MallocDispatch
```

## 概述

应用程序进程可替换/恢复的HiDebug_MallocDispatch表结构类型定义。通过该结构体，开发者可以自定义内存管理函数指针，实现对进程内存分配和释放的监控与定制。主要特点包括：支持动态替换和恢复内存管理函数、提供全面的内存操作接口（malloc、calloc、realloc、free、mmap、munmap）、不影响系统默认内存管理行为。使用场景包括：内存泄漏检测、内存使用性能分析、自定义内存分配策略、内存安全监控等。能够帮助开发者及时发现和解决内存问题，提升应用稳定性和性能。

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

