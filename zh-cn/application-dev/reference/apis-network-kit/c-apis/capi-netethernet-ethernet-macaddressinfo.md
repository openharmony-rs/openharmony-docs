# Ethernet_MacAddressInfo

```c
typedef struct Ethernet_MacAddressInfo {...} Ethernet_MacAddressInfo
```

## 概述

以太网网卡MAC地址信息。

<!--Device-struct Ethernet_MacAddressInfo {...}--><!--Device-struct Ethernet_MacAddressInfo {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**起始版本：** 26.0.0

**相关模块：** [NetEthernet](capi-network-kit-netethernet.md)

**所在头文件：** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char ifaceName[ETHERNET_MAX_STR_LEN] | 以太网网卡名称。<br>**起始版本：** 26.0.0 |
| char macAddr[ETHERNET_MAX_STR_LEN] | 以太网网卡MAC地址。<br>**起始版本：** 26.0.0 |


