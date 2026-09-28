# HiDebug

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=67e03cb5f2694f739f98a438811ea6f4514e5238 translatedAt=2026-09-21T02:34:19.817Z pushedAt=2026-09-22T01:29:30.388Z -->

## Overview

Provides debugging functions. The functions of this module can be used to obtain CPU usage, memory, heap, and capture trace.

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

## Files

| Name| Description|
| -- | -- |
| [hidebug.h](capi-hidebug-h.md) | Defines the debugging functions of the HiDebug module, providing capabilities such as CPU usage monitoring, memory information query, trace capture, stack backtracking, performance sampling, memory export listening, and maintenance and debugging information recording, helping developers perform application performance analysis, resource management, and problem diagnosis. |
| [hidebug_type.h](capi-hidebug-type-h.md) | Defines the structs for the system performance analysis and debugging capabilities provided by the HiDebug module, supporting thread CPU usage statistics, system memory information collection, native memory tracking, stack backtracking analysis, and other functions. It is used in scenarios such as performance optimization, problem diagnosis, and resource monitoring, helping developers quickly locate performance bottlenecks, memory leaks, and other issues. The module design follows a unified data structure specification, provides configuration and callback types for functions such as trace capture and resource collection, and supports multi-dimensional performance data collection and analysis. |
