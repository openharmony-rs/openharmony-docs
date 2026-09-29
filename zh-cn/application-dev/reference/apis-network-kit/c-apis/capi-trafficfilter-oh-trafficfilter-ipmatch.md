# OH_TrafficFilter_IPMatch

```c
union OH_TrafficFilter_IPMatch {...}
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
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) single | 单个IP地址，当type为OH_TRAFFICFILTER_IP_MATCH_SINGLE时使用<br>**起始版本：** 26.0.0 |
| [OH_TrafficFilter_IPCidr](capi-trafficfilter-oh-trafficfilter-ipcidr.md) cidr | CIDR匹配值，当type为OH_TRAFFICFILTER_IP_MATCH_CIDR时使用<br>**起始版本：** 26.0.0 |
| [OH_TrafficFilter_IPRange](capi-trafficfilter-oh-trafficfilter-iprange.md) range | IP范围匹配值，当type为OH_TRAFFICFILTER_IP_MATCH_RANGE时使用<br>**起始版本：** 26.0.0 |
| OH_TrafficFilter_IPMulti multi;
 } value | 多IP匹配值，当type为OH_TRAFFICFILTER_IP_MATCH_MULTI时使用<br>**起始版本：** 26.0.0 |


