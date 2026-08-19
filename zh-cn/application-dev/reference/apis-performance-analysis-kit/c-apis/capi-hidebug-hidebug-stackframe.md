# HiDebug_StackFrame

```c
typedef struct HiDebug_StackFrame {...} HiDebug_StackFrame
```

## 概述

Defines the stack frame content.

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [HiDebug_StackFrameType](capi-hidebug-type-h.md#hidebug_stackframetype) type | Type of the current stack. |
| union | frame content. |
| struct [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) js | Js stack frame defined in [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) |
| struct [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) native; } frame | Native frame defined in [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) |


