# HiDebug_StackFrame

```c
typedef struct HiDebug_StackFrame {...} HiDebug_StackFrame
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
| [HiDebug_StackFrameType](capi-hidebug-type-h.md#hidebug_stackframetype) type | Type of the current stack. |
| union | frame content. |
| struct [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) js | Js stack frame defined in {@link HiDebug_JsStackFrame} |
| struct [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) native;
 } frame | Native frame defined in {@link HiDebug_NativeStackFrame} |


