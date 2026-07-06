# Ethernet_NetAddr

```c
typedef struct Ethernet_NetAddr {...} Ethernet_NetAddr
```

## 概述

网络地址。

**起始版本：** 26.0.0

**相关模块：** [NetEthernet](capi-netethernet.md)

**所在头文件：** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t family |  |
| uint8_t prefixlen |  |
| uint16_t port |  |
| char address[ETHERNET_MAX_STR_LEN] |  |


