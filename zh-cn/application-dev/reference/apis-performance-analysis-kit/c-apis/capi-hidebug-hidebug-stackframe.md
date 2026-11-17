# HiDebug_StackFrame

```c
typedef struct HiDebug_StackFrame {...} HiDebug_StackFrame
```

## 概述

栈帧内容的定义。该结构体用于表示调试时的栈帧信息，支持获取当前栈的类型以及对应的js栈帧或Native栈帧内容，帮助开发者进行问题定位和调试分析。

<!--Device-struct HiDebug_StackFrame {...}--><!--Device-struct HiDebug_StackFrame {...}-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 20

**相关模块：** [HiDebug](capi-performance-analysis-kit-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [HiDebug_StackFrameType](capi-hidebug-type-h.md#hidebug_stackframetype) type | 当前栈的类型。 |
| frame | 栈帧内容。 |
| frame.js | js栈帧，见[HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md)。 |
| frame.native | native栈帧，见[HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md)。 |


