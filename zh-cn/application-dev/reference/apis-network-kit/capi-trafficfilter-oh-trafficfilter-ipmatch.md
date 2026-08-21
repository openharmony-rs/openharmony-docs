# OH_TrafficFilter_IPMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_IPMatch {...} OH_TrafficFilter_IPMatch
```

## 概述

IP匹配条件。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_TrafficFilter_IPMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_ipmatchtype) type | 匹配类型。<br>**起始版本：** 26.0.0 |
| bool invert | 是否反转匹配结果。<br>**起始版本：** 26.0.0 |
| union | 匹配规则。<br>**起始版本：** 26.0.0 |


