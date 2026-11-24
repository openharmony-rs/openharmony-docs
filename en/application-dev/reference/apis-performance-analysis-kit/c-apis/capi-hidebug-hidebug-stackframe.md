# HiDebug_StackFrame

```c
typedef struct HiDebug_StackFrame {...} HiDebug_StackFrame
```

## Overview

Defines the stack frame content.

<!--Device-struct HiDebug_StackFrame {...}--><!--Device-struct HiDebug_StackFrame {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Related module**: [HiDebug](capi-performance-analysis-kit-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [HiDebug_StackFrameType](capi-hidebug-type-h.md#hidebug_stackframetype) type | Type of the current stack.<br><!--Device-HiDebug_StackFrameType type--><!--Device-HiDebug_StackFrameType type-End--> |
| frame.js | Js stack frame defined in [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md)<br><!--Device-frame.js--><!--Device-frame.js-End--> |
| frame.native | Native frame defined in [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md)<br><!--Device-frame.native--><!--Device-frame.native-End--> |


