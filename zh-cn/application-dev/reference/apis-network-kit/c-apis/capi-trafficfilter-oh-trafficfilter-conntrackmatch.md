# OH_TrafficFilter_ConntrackMatch

```c
typedef struct OH_TrafficFilter_ConntrackMatch {...} OH_TrafficFilter_ConntrackMatch
```

## 概述

连接跟踪匹配条件基于连接跟踪状态匹配报文

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 启用连接跟踪匹配<br>**起始版本：** 26.1.0 |
| uint8_t stateMask | 连接状态（使用OH_TRAFFICFILTER_CT_STATE_*位图）<br>**起始版本：** 26.1.0 |


