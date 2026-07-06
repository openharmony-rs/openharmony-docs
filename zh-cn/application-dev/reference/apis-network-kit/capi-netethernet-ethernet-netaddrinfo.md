# Ethernet_NetAddrInfo

```c
typedef struct Ethernet_NetAddrInfo {...} Ethernet_NetAddrInfo
```

## 概述

以太网网卡网络地址信息，包含以太网网卡名称及网络地址信息。

**起始版本：** 26.0.0

**相关模块：** [NetEthernet](capi-netethernet.md)

**所在头文件：** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char ifaceName[ETHERNET_MAX_STR_LEN] |  |
| [Ethernet_NetAddr](capi-netethernet-ethernet-netaddr.md) netAddrInfo[ETHERNET_MAX_NET_SIZE] |  |
| int32_t netAddrInfoSize |  |


