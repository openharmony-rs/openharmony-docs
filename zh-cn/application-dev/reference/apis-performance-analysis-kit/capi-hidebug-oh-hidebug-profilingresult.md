# OH_HiDebug_ProfilingResult

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_HiDebug_ProfilingResult {...} OH_HiDebug_ProfilingResult
```

## 概述

封装单次资源采集的结果。

**起始版本：** 24

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_HiDebug_ResourceType](capi-hidebug-type-h.md#oh_hidebug_resourcetype) resourceType | 资源采集类型。<br> **起始版本：** 24 |
| const char* filePath | 资源采集结果文件路径。如果采集失败则为空值。<br> **起始版本：** 24 |

