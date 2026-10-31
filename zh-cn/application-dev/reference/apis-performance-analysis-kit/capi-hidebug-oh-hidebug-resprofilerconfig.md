# OH_HiDebug_ResProfilerConfig

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_HiDebug_ResProfilerConfig {...} OH_HiDebug_ResProfilerConfig
```

## 概述

定义资源采集配置结构体类型。

**起始版本：** 24

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t maxDuration | 最大采集时长，取值范围为 [1, 3600]，单位为秒。<br>传入参数超出取值范围，接口将返回错误码[HIDEBUG_RES_PROF_INVALID_MAX_DURATION](capi-hidebug-type-h.md#hidebug_errorcode)。<br> **起始版本：** 24 |
| uint32_t filterSize | 过滤大小，取值范围为 [1, 4294967295]，单位为字节。<br>传入参数超出取值范围，接口将返回错误码[HIDEBUG_RES_PROF_INVALID_FILTER_SIZE](capi-hidebug-type-h.md#hidebug_errorcode)。<br> **起始版本：** 24 |
| uint32_t maxStackDepth | 最大栈追踪深度，取值范围为 [0, 30]，单位为帧。建议根据实际需求设置合适的栈深度，深度越大采集开销越大。<br>传入参数超出取值范围，接口将返回错误码[HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode)。<br> **起始版本：** 24 |
| uint32_t statisticsInterval | 统计间隔，取值范围为 [0, 3600]，单位为秒。<br>传入参数超出取值范围，接口将返回错误码[HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode)。<br> **起始版本：** 24 |
| uint32_t sampleInterval | 采样大小，取值范围为 [384, 4294967295]，单位为字节。<br>在采样模式下，如果内存分配大小小于等于采样大小，则概率性采样，否则全量采样。<br>传入参数超出取值范围，接口将返回错误码[HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode)。<br> **起始版本：** 24 |

