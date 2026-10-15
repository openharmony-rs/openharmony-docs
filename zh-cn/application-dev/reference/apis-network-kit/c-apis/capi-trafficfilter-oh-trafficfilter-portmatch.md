# OH_TrafficFilter_PortMatch

```c
struct OH_TrafficFilter_PortMatch {...}
```

## 概述

端口匹配条件。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_TrafficFilter_PortMatchType type | 匹配类型。<br>**起始版本：** 26.0.0 |
| bool invert | 是否反转匹配结果。<br>**起始版本：** 26.0.0 |
| value.single | 单个端口，当type为OH_TRAFFICFILTER_PORT_MATCH_SINGLE时使用<br>**起始版本：** 26.0.0 |
| value.range | 端口范围匹配值，当type为OH_TRAFFICFILTER_PORT_MATCH_RANGE时使用<br>**起始版本：** 26.0.0 |
| value.multi | 多端口匹配值，当type为OH_TRAFFICFILTER_PORT_MATCH_MULTI时使用<br>**起始版本：** 26.0.0 |


