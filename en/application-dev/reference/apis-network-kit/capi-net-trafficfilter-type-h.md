# net_trafficfilter_type.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6a2c2337a178940b8b8b2d0ed4bd22e27108d63c translatedAt=2026-08-12T11:08:31.060Z pushedAt=2026-08-13T05:46:27.904Z -->

## Overview

Declares the common types and error codes required for network traffic filtering and redirection. This header file defines the match condition structs (such as IP addresses, ports, and interfaces) used in traffic filtering and redirection, configuration structs (such as packet filter rules and redirection rules), and error codes returned by operations.<br> This header file is used to construct parameters and parse return values when APIs such as [OH_TrafficFilter_CreateRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_createredirector) are called.

**File to include:** <network/netmanager_ext/net_trafficfilter_type.h>

**Library:** libnet_trafficfilter.so

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module:** [TrafficFilter](capi-trafficfilter.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) | OH_TrafficFilter_IPAddress | Defines an IP address in binary format. Both IPv4 and IPv6 addresses are supported. |
| [OH_TrafficFilter_IPCidr](capi-trafficfilter-oh-trafficfilter-ipcidr.md) | OH_TrafficFilter_IPCidr | Defines an IP address matched by CIDR (Classless Inter-Domain Routing). |
| [OH_TrafficFilter_IPRange](capi-trafficfilter-oh-trafficfilter-iprange.md) | OH_TrafficFilter_IPRange | Defines the IP address range. |
| [OH_TrafficFilter_IPMulti](capi-trafficfilter-oh-trafficfilter-ipmulti.md) | OH_TrafficFilter_IPMulti | Defines multiple IP addresses matched. |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) | OH_TrafficFilter_IPMatch | Defines the IP address match conditions. |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) | OH_TrafficFilter_InterfaceMatch | Defines the interface match conditions. |
| [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) | OH_TrafficFilter_PortRange | Defines the port range. |
| [OH_TrafficFilter_PortMulti](capi-trafficfilter-oh-trafficfilter-portmulti.md) | OH_TrafficFilter_PortMulti | Defines multiple ports matched. |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) | OH_TrafficFilter_PortMatch | Defines the port match conditions. |
| [OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) | OH_TrafficFilter_ConnectionInfo | Defines connection information. This struct describes the five-tuple information of network connection (source IP address, destination IP address, source port, destination port, and protocol type), which is used to query information about the process that starts the connection. Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct (for example, by using memset), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) to the actual size of the struct specified by the caller, which is typically **sizeof(OH_TrafficFilter_ConnectionInfo)**. Binary compatibility rule (ABI (application binary interface), which ensures that the program compiled using the new compiler can correctly read the data structure saved in the memory by the program compiled using the old compiler): The system uses [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) to determine which fields can be safely read. If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) is smaller than the minimum size required by the current interface, the interface returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) is larger than the size known to the system, the excess fields are ignored. |
| [OH_TrafficFilter_ProcessInfo](capi-trafficfilter-oh-trafficfilter-processinfo.md) | OH_TrafficFilter_ProcessInfo | Defines the process information. This struct stores the process information returned by [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess). Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct (for example, by using memset), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) to the actual size of the struct specified by the caller, which is typically **sizeof(OH_TrafficFilter_ConnectionInfo)**. Binary compatibility rule (ABI (application binary interface), which ensures that the program compiled using the new compiler can correctly read the data structure saved in the memory by the program compiled using the old compiler): The system uses [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) to determine which fields can be safely read. If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) is smaller than the minimum size required by the current interface, the interface returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) is larger than the size known to the system, the excess fields are ignored. Output validity rule: When [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess) returns [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode), the fields covered by [size](capi-trafficfilter-oh-trafficfilter-processinfo.md#member-variables) contain valid output values. When the API returns an error code, the caller must not rely on the values of output fields other than [size](capi-trafficfilter-oh-trafficfilter-processinfo.md#member-variables). |
| [OH_TrafficFilter_RedirectRule](capi-trafficfilter-oh-trafficfilter-redirectrule.md) | OH_TrafficFilter_RedirectRule | Defines the traffic redirection rule. This struct defines a TCP traffic redirection rule that redirects matching traffic to a specified proxy server. Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct (for example, by using memset), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) to the actual size of the struct specified by the caller, which is typically **sizeof(OH_TrafficFilter_ConnectionInfo)**. Binary compatibility rule (ABI (application binary interface), which ensures that the program compiled using the new compiler can correctly read the data structure saved in the memory by the program compiled using the old compiler): The system uses [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) to determine which fields can be safely read. If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) is smaller than the minimum size required by the current interface, the interface returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md#member-variables) is larger than the size known to the system, the excess fields are ignored. Failure rule: If [OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule) returns an error code, there is no guarantee that the rule has been added or has taken effect. The caller should check the return value before assuming the rule is in effect. |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md) | OH_TrafficFilter_Redirector | Defines a traffic redirector. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_TrafficFilter_ErrCode](#oh_trafficfilter_errcode) | OH_TrafficFilter_ErrCode | Defines the error codes for traffic filtering and redirection. |
| [OH_TrafficFilter_IPMatchType](#oh_trafficfilter_ipmatchtype) | OH_TrafficFilter_IPMatchType | Defines an IP match type. |
| [OH_TrafficFilter_IPFamily](#oh_trafficfilter_ipfamily) | OH_TrafficFilter_IPFamily | Defines an IP address family. |
| [OH_TrafficFilter_PortMatchType](#oh_trafficfilter_portmatchtype) | OH_TrafficFilter_PortMatchType | Defines a port match type. |
| [OH_TrafficFilter_HookPoint](#oh_trafficfilter_hookpoint) | OH_TrafficFilter_HookPoint | Enumerates the hook points, specifying where the rule takes effect in the network protocol stack. As packets pass through the kernel network protocol stack, hook points are triggered at different stages, and the rule intercepts packets at the corresponding hook points. For example, the INPUT chain processes packets entering the local device, and the OUTPUT chain processes packets sent from the local device. |

### Macros

| Name | Description |
| -- | -- |
| OH_TRAFFICFILTER_IP_ADDRLEN       16 | Maximum length of the IP address byte array (compatible with both IPv4 and IPv6).<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT  16 | Maximum number of IP addresses supported for multi–IP address matching.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT 64 | Maximum number of ports supported for multi-port matching.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_META   0 | NFQueue packet copy mode: copies only metadata.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_PACKET 0xFFFF | NFQueue packet copy mode: copies the entire packet.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_COPY_LEN    0xFFFF | Default length of the copied NFQueue packet, in bytes. If the value is **0xFFFF**, the entire packet is copied; if a smaller value, such as **128**, is used, only the packet header is copied.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_QUEUE_MAXLEN  1024 | Default maximum length of the NFQueue queue (number of packets).<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN  0x1 | NFQueue queue flag: FAIL-OPEN mode. When a user-mode process crashes, the kernel automatically allows packets to pass to avoid network interruption.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_MIN_PRIORITY        1 | Minimum priority.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_MAX_PRIORITY        10000 | Maximum priority.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_MIN_GROUP_ID        1 | Minimum group ID value.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_MAX_GROUP_ID        65535 | Maximum group ID value.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IFNAMSIZ            32 | Maximum length of the network interface name.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ANY           0 | Protocol constant: any protocol.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_TCP           6 | Protocol constant: TCP.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_UDP           17 | Protocol constant: UDP.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ICMP          1 | Protocol constant: ICMP.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ICMPV6        58 | Protocol constant: ICMPv6.<br>**Since:** 26.0.0 |

## Enum Description

### OH_TrafficFilter_ErrCode

```c
enum OH_TrafficFilter_ErrCode
```

**Description**

Defines the error codes for traffic filtering and redirection.

**Since**: 26.0.0

| Value | Description |
| -- | -- |
| OH_TRAFFICFILTER_OK = 0 | Operation succeeded.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_E_BASE = 29410000 | Base value for the error code.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201 | Missing permissions.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101) | Parameter error (invalid priority, IP address, port, or group ID).<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102) | Resource not found (rule, target, process, or group ID not found).<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103) | Too many rules.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104) | Group ID already in use.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105) | NFQueue error (initialization failed or no available queue).<br>**Since:** 26.0.0 |

### OH_TrafficFilter_IPMatchType

```c
enum OH_TrafficFilter_IPMatchType
```

**Description**

Defines an IP match type.

**Since**: 26.0.0

| Value | Description |
| -- | -- |
| OH_TRAFFICFILTER_IP_MATCH_ANY = 0 | Any IP address.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_SINGLE = 1 | Single IP address.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_CIDR = 2 | CIDR (for example, **192.168.1.0/24**, which matches all IP addresses in the subnet).<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_RANGE = 3 | IP address range.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_MULTI = 4 | Multiple IP addresses.<br>**Since:** 26.0.0 |

### OH_TrafficFilter_IPFamily

```c
enum OH_TrafficFilter_IPFamily
```

**Description**

Defines an IP address family.

**Since**: 26.0.0

| Value | Description |
| -- | -- |
| OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0 | Unspecified IP address family.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IP_FAMILY_V4 = 1 | IPv4 address family.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_IP_FAMILY_V6 = 2 | IPv6 address family.<br>**Since:** 26.0.0 |

### OH_TrafficFilter_PortMatchType

```c
enum OH_TrafficFilter_PortMatchType
```

**Description**

Defines a port match type.

**Since**: 26.0.0

| Value | Description |
| -- | -- |
| OH_TRAFFICFILTER_PORT_MATCH_ANY = 0 | Any port.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PORT_MATCH_SINGLE = 1 | Single port.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PORT_MATCH_RANGE = 2 | Port range.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_PORT_MATCH_MULTI = 3 | Multiple ports.<br>**Since:** 26.0.0 |

### OH_TrafficFilter_HookPoint

```c
enum OH_TrafficFilter_HookPoint
```

**Description**

Enumerates the hook points, specifying where the rule takes effect in the network protocol stack. As packets pass through the kernel network protocol stack, hook points are triggered at different stages, and the rule intercepts packets at the corresponding hook points. For example, the INPUT chain processes packets entering the local device, and the OUTPUT chain processes packets sent from the local device.

**Since**: 26.0.0

| Enum Item | Description |
| -- | -- |
| OH_TRAFFICFILTER_HOOK_INPUT = 0 | INPUT chain that processes packets received by the local host.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_OUTPUT = 1 | OUTPUT chain that processes packets sent from the local host.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_FORWARD = 2 | FORWARD chain that processes packets forwarded by the local host.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_PREROUTING = 3 | PREROUTING chain that processes packets that have arrived at the NIC but not been routed.<br>**Since:** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_POSTROUTING = 4 | POSTROUTING chain that processes packets about to be sent from the NIC.<br>**Since:** 26.0.0 |
<!--no_check-->