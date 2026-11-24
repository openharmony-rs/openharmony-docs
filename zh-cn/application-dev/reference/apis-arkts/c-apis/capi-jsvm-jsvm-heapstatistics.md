# JSVM_HeapStatistics

```c
typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics
```

## 概述

用于保存有关JavaScript堆内存使用情况的统计信息。

<!--Device-typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics--><!--Device-typedef struct JSVM_HeapStatistics {...} JSVM_HeapStatistics-End-->

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 12

**相关模块：** [JSVM](capi-arkts-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t totalHeapSize | 总堆大小，单位KB。<br><!--Device-size_t totalHeapSize--><!--Device-size_t totalHeapSize-End--> |
| size_t totalHeapSizeExecutable | 可执行堆的总大小，单位KB。<br><!--Device-size_t totalHeapSizeExecutable--><!--Device-size_t totalHeapSizeExecutable-End--> |
| size_t totalPhysicalSize | 总的物理内存大小，单位KB。<br><!--Device-size_t totalPhysicalSize--><!--Device-size_t totalPhysicalSize-End--> |
| size_t totalAvailableSize | 总的可用内存大小，单位KB。<br><!--Device-size_t totalAvailableSize--><!--Device-size_t totalAvailableSize-End--> |
| size_t usedHeapSize | 已使用的堆大小，单位KB。<br><!--Device-size_t usedHeapSize--><!--Device-size_t usedHeapSize-End--> |
| size_t heapSizeLimit | 堆大小限制，单位KB。<br><!--Device-size_t heapSizeLimit--><!--Device-size_t heapSizeLimit-End--> |
| size_t mallocedMemory | 已分配内存的大小，单位KB。<br><!--Device-size_t mallocedMemory--><!--Device-size_t mallocedMemory-End--> |
| size_t externalMemory | 外部内存大小，单位KB。<br><!--Device-size_t externalMemory--><!--Device-size_t externalMemory-End--> |
| size_t peakMallocedMemory | 最大可分配内存的大小，单位KB。<br><!--Device-size_t peakMallocedMemory--><!--Device-size_t peakMallocedMemory-End--> |
| size_t numberOfNativeContexts | 表示当前活跃的native上下文的数量，该数值一直增加可能指示存在内存泄漏。<br><!--Device-size_t numberOfNativeContexts--><!--Device-size_t numberOfNativeContexts-End--> |
| size_t numberOfDetachedContexts | 表示已经脱离的上下文数量。<br><!--Device-size_t numberOfDetachedContexts--><!--Device-size_t numberOfDetachedContexts-End--> |
| size_t totalGlobalHandlesSize | 全局Handle的总大小，单位KB。<br><!--Device-size_t totalGlobalHandlesSize--><!--Device-size_t totalGlobalHandlesSize-End--> |
| size_t usedGlobalHandlesSize | 已经使用的全局Handle的大小，单位KB。<br><!--Device-size_t usedGlobalHandlesSize--><!--Device-size_t usedGlobalHandlesSize-End--> |


