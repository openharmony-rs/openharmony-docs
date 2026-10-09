# HiDebug_Backtrace_Object__*

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e927796ba68acb42b31a64400ef3f800e94a271e translatedAt=2026-09-16T10:41:40.846Z pushedAt=2026-09-20T09:01:52.239Z -->

```c
typedef struct HiDebug_Backtrace_Object__* HiDebug_Backtrace_Object
```

## Overview

Defines an object used for stack backtrace and stack parsing. This object encapsulates the context information required for stack backtrace, including data such as call stack addresses and thread states. Through related interfaces, you can obtain detailed stack frame information and symbol resolution results. This object is created through **HiDebug**-related interfaces. After use, call the corresponding destroy interface to release resources.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

