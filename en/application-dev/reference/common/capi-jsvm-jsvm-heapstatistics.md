# JSVM_HeapStatistics

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:51.842Z pushedAt=2026-06-22T03:21:12.878Z -->

```c
typedef struct {...} JSVM_HeapStatistics
```

## Overview

Stores statistics about JavaScript heap memory usage.

**Use scenario:** Performance monitoring: monitor the heap memory usage of an application in real time and evaluate the memory footprint. Memory optimization: identify memory usage bottlenecks and optimize memory configuration by analyzing heap memory data. Memory leak detection: assist in discovering potential memory leak issues through fields such as **numberOfNativeContexts**.

**Problem solved:** Helping developers understand the memory usage of an application; providing data support for performance optimization and memory management; and facilitating the investigation and analysis of memory issues.

**Benefits:** Improving the memory usage efficiency of an application; reducing the cost of investigating memory-related issues; enhancing the overall performance and stability of the application.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t totalHeapSize | Total heap size, in KB. |
| size_t totalHeapSizeExecutable | Total executable heap size, in KB. |
| size_t totalPhysicalSize | Total physical memory size, in KB. |
| size_t totalAvailableSize | Total available memory size, in KB. |
| size_t usedHeapSize | Used heap size, in KB. |
| size_t heapSizeLimit | Heap size limit, in KB. |
| size_t mallocedMemory | Allocated memory size, in KB. |
| size_t externalMemory | External memory size, in KB. |
| size_t peakMallocedMemory | Peak allocated memory size, in KB. |
| size_t numberOfNativeContexts | Number of active native contexts. If the value keeps increasing, memory leaks may occur.|
| size_t numberOfDetachedContexts | Number of detached contexts.|
| size_t totalGlobalHandlesSize | Total global handle size, in KB. |
| size_t usedGlobalHandlesSize | Used global handle size, in KB. |