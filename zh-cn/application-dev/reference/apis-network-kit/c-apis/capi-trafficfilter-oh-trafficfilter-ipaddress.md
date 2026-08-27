# OH_TrafficFilter_IPAddress

```c
typedef struct OH_TrafficFilter_IPAddress {...} OH_TrafficFilter_IPAddress
```

## 概述

二进制形式的IP地址，支持IPv4和IPv6。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_TrafficFilter_IPFamily](capi-net-trafficfilter-type-h.md#oh_trafficfilter_ipfamily) family | 地址族。若未显式设置，默认使用IPv4。<br>**起始版本：** 26.0.0 |
| uint8_t addr[OH_TRAFFICFILTER_IP_ADDRLEN] | IP地址字节。字节必须以网络字节序存储。对于IPv4，{@link addr}[0]到{@link addr}[3]存储IPv4地址，{@link addr}[4]到{@link addr}[15]必须设置为0。对于IPv6，{@link addr}[0]到{@link addr}[15]存储IPv6地址。如果字节与{@link family}要求的地址布局不匹配，使用该结构体的接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。<br>**起始版本：** 26.0.0 |


