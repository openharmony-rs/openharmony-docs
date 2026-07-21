# Ethernet_NetAddr

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

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
| uint8_t family | 网络地址族。IPv4 = 1，IPv6 = 2。 |
| uint8_t prefixlen | 前缀长度。 |
| uint16_t port | 端口号。 |
| char address[ETHERNET_MAX_STR_LEN] | IP地址。 |


