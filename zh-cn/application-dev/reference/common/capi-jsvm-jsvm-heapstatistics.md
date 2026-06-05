# JSVM_HeapStatistics
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_HeapStatistics
```

## 概述

用于保存有关JavaScript堆内存使用情况的统计信息。

**使用场景：** 性能监控：实时监测应用的堆内存使用情况，评估内存占用水平。内存优化：通过分析堆内存数据，识别内存使用瓶颈，优化内存配置。内存泄漏检测：通过numberOfNativeContexts等字段，辅助发现潜在的内存泄漏问题。

**解决问题：** 帮助开发者了解应用的内存使用状况，为性能优化和内存管理提供数据支撑，支持内存问题的排查和分析。

**收益：** 提升应用的内存使用效率，降低内存相关问题的排查成本，改善应用的整体性能和稳定性。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 12

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t totalHeapSize | 总堆大小，单位KB。 |
| size_t totalHeapSizeExecutable | 可执行堆的总大小，单位KB。 |
| size_t totalPhysicalSize | 总的物理内存大小，单位KB。 |
| size_t totalAvailableSize | 总的可用内存大小，单位KB。 |
| size_t usedHeapSize | 已使用的堆大小，单位KB。 |
| size_t heapSizeLimit | 堆大小限制，单位KB。 |
| size_t mallocedMemory | 已分配内存的大小，单位KB。 |
| size_t externalMemory | 外部内存大小，单位KB。 |
| size_t peakMallocedMemory | 最大可分配内存的大小，单位KB。 |
| size_t numberOfNativeContexts | 表示当前活跃的native上下文的数量，该数值一直增加可能指示存在内存泄漏。 |
| size_t numberOfDetachedContexts | 表示已经脱离的上下文数量。 |
| size_t totalGlobalHandlesSize | 全局Handle的总大小，单位KB。 |
| size_t usedGlobalHandlesSize | 已经使用的全局Handle的大小，单位KB。 |


