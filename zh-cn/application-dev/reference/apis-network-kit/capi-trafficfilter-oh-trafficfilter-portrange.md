# OH_TrafficFilter_PortRange

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_PortRange {...} OH_TrafficFilter_PortRange
```

## 概述

范围匹配的端口匹配值。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint16_t startPort | 范围的起始端口。<br>**起始版本：** 26.0.0 |
| uint16_t endPort | 范围的结束端口。<br>**起始版本：** 26.0.0 |


