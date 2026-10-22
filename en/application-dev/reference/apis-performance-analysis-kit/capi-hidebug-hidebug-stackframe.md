# HiDebug_StackFrame

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e927796ba68acb42b31a64400ef3f800e94a271e translatedAt=2026-09-16T10:45:34.149Z pushedAt=2026-09-20T09:01:52.245Z -->

```c
typedef struct HiDebug_StackFrame {...} HiDebug_StackFrame
```

## Overview

Defines the stack frame content. This structure represents the stack frame information during debugging. It supports obtaining the current stack type and the corresponding JS stack frame or Native stack frame content, helping developers locate issues and perform debugging analysis.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [HiDebug_StackFrameType](capi-hidebug-type-h.md#hidebug_stackframetype) type | Type of the current stack.                                        |
| struct [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md) js       | JS stack frame content defined by [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md).        |
| struct [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md) native                                   | Native stack frame content defined by [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md).|


