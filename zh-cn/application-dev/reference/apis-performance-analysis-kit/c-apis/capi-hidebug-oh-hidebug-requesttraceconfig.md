# OH_HiDebug_RequestTraceConfig

```c
typedef struct OH_HiDebug_RequestTraceConfig {...} OH_HiDebug_RequestTraceConfig
```

## 概述

请求trace采集的配置结构类型定义。用于在应用性能分析和调试场景中配置trace采集参数，如定位应用启动慢、UI卡顿、CPU占用高等性能问题。

**起始版本：** 24

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* identifier |  |
| uint32_t bufferSizeKb |  |
| uint32_t durationMs |  |
| uint32_t reserved |  |


