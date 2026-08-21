# OH_TrafficFilter_PortMulti

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_PortMulti {...} OH_TrafficFilter_PortMulti
```

## 概述

多端口匹配的端口匹配值。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t portCount | 数组中的端口数量。<br>**起始版本：** 26.0.0 |
| uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT] | 端口数组。<br>**起始版本：** 26.0.0 |


