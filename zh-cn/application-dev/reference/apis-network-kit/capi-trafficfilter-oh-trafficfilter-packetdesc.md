# OH_TrafficFilter_PacketDesc

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_PacketDesc {...} OH_TrafficFilter_PacketDesc
```

## 概述

报文描述符。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t packetId | 报文ID（报文到达netfilter（Network Filter，网络过滤器）时由内核分配）。 |
| uint8_t protocol | 协议类型。 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | 源IP地址（支持IPv4和IPv6）。 |
| uint16_t srcPort | 源端口。 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | 目的IP地址（支持IPv4和IPv6）。 |
| uint16_t dstPort | 目的端口。 |
| uint32_t packetLen | 报文长度。 |
| uint8_t* data | 报文数据指针（用户可修改，内存由系统管理，**仅在回调期间有效，回调返回后不可再访问该指针**）。 |
| void* userData | 用户数据（在回调中使用）。 |
