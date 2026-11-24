# JSVM_HeapStatistics

```c
typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics
```

## Overview

Heap statisics.

<!--Device-typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics--><!--Device-typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t totalHeapSize | the size of the total heap.<br><!--Device-size_t totalHeapSize--><!--Device-size_t totalHeapSize-End--> |
| size_t totalHeapSizeExecutable | the executable size of the total heap.<br><!--Device-size_t totalHeapSizeExecutable--><!--Device-size_t totalHeapSizeExecutable-End--> |
| size_t totalPhysicalSize | the physical size of the total heap.<br><!--Device-size_t totalPhysicalSize--><!--Device-size_t totalPhysicalSize-End--> |
| size_t totalAvailableSize | the available size of the total heap.<br><!--Device-size_t totalAvailableSize--><!--Device-size_t totalAvailableSize-End--> |
| size_t usedHeapSize | used size of the heap.<br><!--Device-size_t usedHeapSize--><!--Device-size_t usedHeapSize-End--> |
| size_t heapSizeLimit | heap size limit.<br><!--Device-size_t heapSizeLimit--><!--Device-size_t heapSizeLimit-End--> |
| size_t mallocedMemory | memory requested by the heap.<br><!--Device-size_t mallocedMemory--><!--Device-size_t mallocedMemory-End--> |
| size_t externalMemory | heap-requested external memory.<br><!--Device-size_t externalMemory--><!--Device-size_t externalMemory-End--> |
| size_t peakMallocedMemory | peak memory requested by the heap.<br><!--Device-size_t peakMallocedMemory--><!--Device-size_t peakMallocedMemory-End--> |
| size_t numberOfNativeContexts | the number of native contexts.<br><!--Device-size_t numberOfNativeContexts--><!--Device-size_t numberOfNativeContexts-End--> |
| size_t numberOfDetachedContexts | the number of detached contexts.<br><!--Device-size_t numberOfDetachedContexts--><!--Device-size_t numberOfDetachedContexts-End--> |
| size_t totalGlobalHandlesSize | the size of the total global handles.<br><!--Device-size_t totalGlobalHandlesSize--><!--Device-size_t totalGlobalHandlesSize-End--> |
| size_t usedGlobalHandlesSize | the size of the used global handles.<br><!--Device-size_t usedGlobalHandlesSize--><!--Device-size_t usedGlobalHandlesSize-End--> |


