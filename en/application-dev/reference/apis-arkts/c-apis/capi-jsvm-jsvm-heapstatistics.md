# JSVM_HeapStatistics

```c
typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics
```

## Overview

Heap statisics.

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t totalHeapSize | the size of the total heap. |
| size_t totalHeapSizeExecutable | the executable size of the total heap. |
| size_t totalPhysicalSize | the physical size of the total heap. |
| size_t totalAvailableSize | the available size of the total heap. |
| size_t usedHeapSize | used size of the heap. |
| size_t heapSizeLimit | heap size limit. |
| size_t mallocedMemory | memory requested by the heap. |
| size_t externalMemory | heap-requested external memory. |
| size_t peakMallocedMemory | peak memory requested by the heap. |
| size_t numberOfNativeContexts | the number of native contexts. |
| size_t numberOfDetachedContexts | the number of detached contexts. |
| size_t totalGlobalHandlesSize | the size of the total global handles. |
| size_t usedGlobalHandlesSize | the size of the used global handles. |


