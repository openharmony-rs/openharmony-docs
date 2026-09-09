# OH_TrafficFilter_PacketDecision

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef enum OH_TrafficFilter_PacketDecision {...} OH_TrafficFilter_PacketDecision
```

## 概述

报文处理决策类型。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 枚举项

| 名称 | 说明 |
| -- | -- |
| OH_TRAFFICFILTER_DECISION_ACCEPT = 0 | 接受报文。 |
| OH_TRAFFICFILTER_DECISION_DROP | 丢弃报文。 |
