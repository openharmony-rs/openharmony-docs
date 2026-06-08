# JSVM_CpuProfiler__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_CpuProfiler__* JSVM_CpuProfiler
```

## 概述

表示一个JavaScript CPU时间性能分析器。

**使用场景：** 分析JavaScript应用或模块的CPU使用情况，定位性能热点和性能瓶颈，优化JavaScript代码执行效率。

**功能特点：** 提供详细的CPU时间分析数据，支持函数级别的性能统计，可生成性能分析报告。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 12

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

