# HiDebug_StackFrame

```c
struct HiDebug_StackFrame {...}
```

## Overview

Defines the stack frame content.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| HiDebug_StackFrameType type | Type of the current stack. |
| frame.js | Js stack frame defined in [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) |
| frame.native | Native frame defined in [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) |


