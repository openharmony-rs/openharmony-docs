# OH_HiDebug_ProfilingResult

```c
struct OH_HiDebug_ProfilingResult {...}
```

## 概述

封装单次资源采集的结果。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 24

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_HiDebug_ResourceType](capi-hidebug-type-h.md#oh_hidebug_resourcetype) resourceType | Profiled resource type.<br>**起始版本：** 24 |
| const char* filePath | 资源采集结果文件路径，如果采集失败则结果文件路径指针为空。<br>**起始版本：** 24 |


