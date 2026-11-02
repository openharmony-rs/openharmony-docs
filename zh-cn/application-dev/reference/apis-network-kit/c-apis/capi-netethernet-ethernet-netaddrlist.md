# Ethernet_NetAddrList

```c
struct Ethernet_NetAddrList {...}
```

## 概述

以太网网卡网络地址列表。

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**起始版本：** 26.0.0

**相关模块：** [NetEthernet](capi-others-netethernet.md)

**所在头文件：** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Ethernet_NetAddrInfo](capi-netethernet-ethernet-netaddrinfo.md) netAddrList[ETHERNET_MAX_NET_SIZE] | 以太网网络地址列表。<br>**起始版本：** 26.0.0 |
| int32_t netAddrListSize | netAddrList的实际大小。<br>**起始版本：** 26.0.0 |


