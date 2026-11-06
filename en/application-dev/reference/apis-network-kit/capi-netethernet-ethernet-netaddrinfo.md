# Ethernet_NetAddrInfo

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=91d29d346031c525e80e74559440427fdd76d0ca translatedAt=2026-08-12T09:53:22.389Z pushedAt=2026-08-12T10:56:07.262Z -->

```c
typedef struct Ethernet_NetAddrInfo {...} Ethernet_NetAddrInfo
```

## Overview

Defines the network address of the Ethernet NIC, including the Ethernet NIC name and the network address information.

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

**File to include:** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| char ifaceName[ETHERNET_MAX_STR_LEN] | Ethernet NIC name. |
| [Ethernet_NetAddr](capi-netethernet-ethernet-netaddr.md) netAddrInfo[ETHERNET_MAX_NET_SIZE] | Network address. |
| int32_t netAddrInfoSize | Actual size of the **netAddrInfo** array. |