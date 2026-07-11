# HiDebug_StackFrame

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiDebug_StackFrame {...} HiDebug_StackFrame
```

## 概述

栈帧内容的定义。该结构体用于表示调试时的栈帧信息，支持获取当前栈的类型以及对应的js栈帧或Native栈帧内容，帮助开发者进行问题定位和调试分析。

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [HiDebug_StackFrameType](capi-hidebug-type-h.md#hidebug_stackframetype) type | 当前栈的类型。                                         |
| struct [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) js       | 由[HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md)定义的js栈帧内容。         |
| struct [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) native                                   | 由[HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md)定义的native栈帧内容。 |


