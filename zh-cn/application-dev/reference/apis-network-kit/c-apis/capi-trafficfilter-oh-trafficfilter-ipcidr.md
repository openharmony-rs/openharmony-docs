# OH_TrafficFilter_IPCidr

```c
typedef struct OH_TrafficFilter_IPCidr {...} OH_TrafficFilter_IPCidr
```

## 概述

CIDR（Classless Inter-Domain Routing，无类别域间路由）匹配的IP匹配值。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) base | CIDR块的基IP地址。<br>**起始版本：** 26.0.0 |
| uint8_t prefixLen | CIDR前缀长度。<br>**起始版本：** 26.0.0 |


