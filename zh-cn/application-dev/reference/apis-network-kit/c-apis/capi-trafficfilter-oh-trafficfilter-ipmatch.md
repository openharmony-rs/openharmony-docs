# OH_TrafficFilter_IPMatch

```c
struct OH_TrafficFilter_IPMatch {...}
```

## 概述

IP匹配条件。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_TrafficFilter_IPMatchType type | 匹配类型。<br>**起始版本：** 26.0.0 |
| bool invert | 是否反转匹配结果。<br>**起始版本：** 26.0.0 |
| value.single | 单个IP地址，当type为OH_TRAFFICFILTER_IP_MATCH_SINGLE时使用<br>**起始版本：** 26.0.0 |
| value.cidr | CIDR匹配值，当type为OH_TRAFFICFILTER_IP_MATCH_CIDR时使用<br>**起始版本：** 26.0.0 |
| value.range | IP范围匹配值，当type为OH_TRAFFICFILTER_IP_MATCH_RANGE时使用<br>**起始版本：** 26.0.0 |
| value.multi | 多IP匹配值，当type为OH_TRAFFICFILTER_IP_MATCH_MULTI时使用<br>**起始版本：** 26.0.0 |


