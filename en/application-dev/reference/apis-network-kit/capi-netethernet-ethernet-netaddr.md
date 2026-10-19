# Ethernet_NetAddr

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=91d29d346031c525e80e74559440427fdd76d0ca translatedAt=2026-08-12T09:53:22.763Z pushedAt=2026-08-12T10:56:07.264Z -->

```c
typedef struct Ethernet_NetAddr {...} Ethernet_NetAddr
```

## Overview

Defines a network address.

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

**File to include:** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t family | Network address family. IPv4 = 1, IPv6 = 2. |
| uint8_t prefixlen | Prefix length. |
| uint16_t port | Port number. |
| char address[ETHERNET_MAX_STR_LEN] | IP address. |