# Ethernet_NetAddr

```c
struct Ethernet_NetAddr {...}
```

## 概述

网络地址。

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**起始版本：** 26.0.0

**相关模块：** [NetEthernet](capi-others-netethernet.md)

**所在头文件：** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t family | 网络地址族。IPv4 = 1，IPv6 = 2。<br>**起始版本：** 26.0.0 |
| uint8_t prefixlen | 前缀长度。<br>**起始版本：** 26.0.0 |
| uint16_t port | 端口号。<br>**起始版本：** 26.0.0 |
| char address[ETHERNET_MAX_STR_LEN] | IP地址。<br>**起始版本：** 26.0.0 |


