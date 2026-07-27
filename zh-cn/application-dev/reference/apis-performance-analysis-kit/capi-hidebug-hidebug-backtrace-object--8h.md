# HiDebug_Backtrace_Object__*

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiDebug_Backtrace_Object__* HiDebug_Backtrace_Object
```

## 概述

用于栈回溯及栈解析的对象。该对象封装了栈回溯所需的上下文信息，包括调用栈地址、线程状态等数据，通过相关接口可获取详细的栈帧信息和符号解析结果。该对象通过HiDebug相关接口创建，使用后需要调用对应的销毁接口释放资源。

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

