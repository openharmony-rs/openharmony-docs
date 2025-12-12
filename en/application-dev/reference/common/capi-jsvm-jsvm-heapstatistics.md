# JSVM_HeapStatistics
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Stores statistics about JavaScript heap memory usage.

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
