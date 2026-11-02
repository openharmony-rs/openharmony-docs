# Ethernet_MacAddrInfoList

```c
struct Ethernet_MacAddrInfoList {...}
```

## 概述

以太网网卡MAC地址信息列表。

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**起始版本：** 26.0.0

**相关模块：** [NetEthernet](capi-others-netethernet.md)

**所在头文件：** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Ethernet_MacAddressInfo](capi-netethernet-ethernet-macaddressinfo.md) macInfoList[ETHERNET_MAX_NET_SIZE] | 以太网网卡MAC地址列表。<br>**起始版本：** 26.0.0 |
| int32_t macInfoListSize | macInfoList数组的实际大小。<br>**起始版本：** 26.0.0 |


