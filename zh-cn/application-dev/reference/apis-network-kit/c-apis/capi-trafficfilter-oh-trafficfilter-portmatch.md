# OH_TrafficFilter_PortMatch

```c
typedef struct OH_TrafficFilter_PortMatch {...} OH_TrafficFilter_PortMatch
```

## 概述

端口匹配条件。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_TrafficFilter_PortMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_portmatchtype) type | 匹配类型。<br>**起始版本：** 26.0.0 |
| bool invert | 是否反转匹配结果。<br>**起始版本：** 26.0.0 |
| union | 匹配规则<br>**起始版本：** 26.0.0 |
| uint16_t single | 单个端口，当type为OH_TRAFFICFILTER_PORT_MATCH_SINGLE时使用<br>**起始版本：** 26.0.0 |
| [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) range | 端口范围匹配值，当type为OH_TRAFFICFILTER_PORT_MATCH_RANGE时使用<br>**起始版本：** 26.0.0 |
| OH_TrafficFilter_PortMulti multi; } value | 多端口匹配值，当type为OH_TRAFFICFILTER_PORT_MATCH_MULTI时使用<br>**起始版本：** 26.0.0 |


