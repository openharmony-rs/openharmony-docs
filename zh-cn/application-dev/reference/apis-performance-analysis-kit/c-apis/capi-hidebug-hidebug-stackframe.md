# HiDebug_StackFrame

```c
union HiDebug_StackFrame {...}
```

## 概述

栈帧内容的定义。该结构体用于表示调试时的栈帧信息，支持获取当前栈的类型以及对应的js栈帧或Native栈帧内容，帮助开发者进行问题定位和调试分析。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**起始版本：** 20

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [struct HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) js | Js stack frame defined in [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) |
| struct HiDebug_NativeStackFrame native;
 } frame | Native frame defined in [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) |


