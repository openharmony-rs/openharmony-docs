# HiDebug_SystemMemInfo

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiDebug_SystemMemInfo {...} HiDebug_SystemMemInfo
```

## 概述

系统内存信息结构类型定义。用于获取系统内存的总量、空闲量、可用量等关键信息，适用于系统性能分析、内存监控、故障诊断等场景，帮助开发者了解系统内存使用状况，优化内存管理策略。

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t totalMem | 系统总的内存，以KB为单位。 |
| uint32_t freeMem | 系统空闲的内存，以KB为单位。 |
| uint32_t availableMem | 系统可用的内存，以KB为单位。 |


