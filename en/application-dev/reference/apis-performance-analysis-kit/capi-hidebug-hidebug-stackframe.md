# HiDebug_StackFrame

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1821c5a567ccf5560c729461b55189633a21be94 translatedAt=2026-11-03T06:12:59.973Z pushedAt=2026-11-03T12:08:25.603Z nl=1 -->

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
| HiDebug_StackFrameType type | Type of the current stack. |
| frame.js       | JS stack frame content defined by [HiDebug_JsStackFrame](capi-hidebug-hidebug-jsstackframe.md). |
| frame.native                                   | Native stack frame content defined by [HiDebug_NativeStackFrame](capi-hidebug-hidebug-nativestackframe.md). |


