# OH_TrafficFilter_PacketDesc

```c
typedef struct OH_TrafficFilter_PacketDesc {...} OH_TrafficFilter_PacketDesc
```

## 概述

报文描述符包含五元组信息和报文数据

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t packetId | 报文ID（报文到达netfilter时由内核分配）<br>**起始版本：** 26.1.0 |
| uint8_t protocol | 协议类型<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | 源IP地址（支持IPv4和IPv6）<br>**起始版本：** 26.1.0 |
| uint16_t srcPort | 源端口<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | 目的IP地址（支持IPv4和IPv6）<br>**起始版本：** 26.1.0 |
| uint16_t dstPort | 目的端口<br>**起始版本：** 26.1.0 |
| uint32_t packetLen | 报文长度<br>**起始版本：** 26.1.0 |
| uint8_t* data | 报文数据指针（用户可修改，内存由系统管理，仅在回调期间有效）<br>**起始版本：** 26.1.0 |
| void* userData | 用户数据（在回调中使用）<br>**起始版本：** 26.1.0 |


