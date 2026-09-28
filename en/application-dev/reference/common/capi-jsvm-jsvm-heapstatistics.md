# JSVM_HeapStatistics

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:31.976Z pushedAt=2026-08-27T06:39:56.710Z -->

```c
typedef struct {...} JSVM_HeapStatistics
```

## Overview

Stores statistics about JavaScript heap memory usage.

**Use scenario**: Performance monitoring: monitors the heap memory usage of an app in real time to evaluate its memory footprint. Memory optimization: analyzes heap memory data to identify memory usage bottlenecks and optimize memory configuration. Memory leak detection: uses fields such as **numberOfNativeContexts** to help identify potential memory leaks.

**Problem solved**: Helps developers understand the memory usage of an app, provides data support for performance optimization and memory management, and supports the troubleshooting and analysis of memory issues.

**Benefit**: Improves the memory usage efficiency of an app, reduces the cost of troubleshooting memory-related issues, and enhances the overall performance and stability of the app.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t totalHeapSize | Total heap size, in KB.|
| size_t totalHeapSizeExecutable | Total size of the executable heap, in KB.|
| size_t totalPhysicalSize | Total physical memory size, in KB.|
| size_t totalAvailableSize | Total available memory size, in KB.|
| size_t usedHeapSize | Used heap size, in KB.|
| size_t heapSizeLimit | Heap size limit, in KB.|
| size_t mallocedMemory | Allocated memory size, in KB.|
| size_t externalMemory | External memory size, in KB.|
| size_t peakMallocedMemory | Maximum size of the memory that can be allocated, in KB.|
| size_t numberOfNativeContexts | Number of active native contexts. If the value keeps increasing, memory leaks may occur.|
| size_t numberOfDetachedContexts | Number of detached contexts.|
| size_t totalGlobalHandlesSize | Total size of global handles, in KB.|
| size_t usedGlobalHandlesSize | Size of the used global handles, in KB.|