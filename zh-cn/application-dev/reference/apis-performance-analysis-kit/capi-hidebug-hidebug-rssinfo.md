# HiDebug_NativeMemInfo

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @leiguangyu-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiDebug_RssInfo {...} HiDebug_RssInfo
```

## 概述

应用程序进程使用的物理内存信息结构类型定义。

**起始版本：** 24

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t rss | 进程常驻集内存大小，以KB为单位。 |
| uint64_t swapRss | 进程换出到交换分区的内存大小，以KB为单位。 |

