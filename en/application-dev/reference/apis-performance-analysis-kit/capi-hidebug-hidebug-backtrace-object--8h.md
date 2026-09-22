# HiDebug_Backtrace_Object__*

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e927796ba68acb42b31a64400ef3f800e94a271e translatedAt=2026-09-21T02:29:35.601Z pushedAt=2026-09-22T01:29:30.373Z -->

```c
typedef struct HiDebug_Backtrace_Object__* HiDebug_Backtrace_Object
```

## Overview

Defines the object used for stack backtrace and stack parsing. This object encapsulates the context information required for stack backtrace, including data such as call stack addresses and thread states. Detailed stack frame information and symbol parsing results can be obtained through related interfaces. This object is created through HiDebug-related interfaces and must be released by calling the corresponding destruction interface after use.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

