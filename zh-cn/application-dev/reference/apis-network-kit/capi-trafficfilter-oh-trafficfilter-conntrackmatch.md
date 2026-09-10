# OH_TrafficFilter_ConntrackMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_ConntrackMatch {...} OH_TrafficFilter_ConntrackMatch
```

## 概述

连接跟踪（Connection Tracking）匹配条件。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 是否启用连接跟踪匹配，true表示启用连接跟踪匹配，false表示不启用连接跟踪匹配。 |
| uint8_t stateMask | 连接状态。 |