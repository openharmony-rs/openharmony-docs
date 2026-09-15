# Ethernet_NetAddrList

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=91d29d346031c525e80e74559440427fdd76d0ca translatedAt=2026-08-12T09:53:25.081Z pushedAt=2026-08-12T10:56:07.270Z -->

```c
typedef struct Ethernet_NetAddrList {...} Ethernet_NetAddrList
```

## Overview

Defines the network address list of Ethernet NICs.

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

**File to include:** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [Ethernet_NetAddrInfo](capi-netethernet-ethernet-netaddrinfo.md) netAddrList[ETHERNET_MAX_NET_SIZE] | Network address list of Ethernet NICs. |
| int32_t netAddrListSize | Actual size of **netAddrList**. |