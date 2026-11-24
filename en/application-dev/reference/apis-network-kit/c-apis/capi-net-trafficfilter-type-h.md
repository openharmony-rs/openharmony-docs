# net_trafficfilter_type.h

## Overview

Declares the common types and error codes required for network traffic filtering and redirection. This header file defines the matching condition structs for IP address, port, MAC address, interface, TCP flags, and connection tracking used in traffic filtering and redirection, the configuration structs for packet filtering rules, redirection rules, and NFQueue configuration, as well as the packet descriptor, packet processing decision, packet copy mode, and error codes returned by operations. <br>Applicable to constructing parameters and parsing return values when calling APIs such as [OH_TrafficFilter_CreateRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_createredirector) or [OH_TrafficFilter_CreatePacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller).

**Library**: libnet_trafficfilter.so

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) | OH_TrafficFilter_IPAddress | Defines an IP address in binary form, supporting both IPv4 and IPv6. |
| [OH_TrafficFilter_IPCidr](capi-trafficfilter-oh-trafficfilter-ipcidr.md) | OH_TrafficFilter_IPCidr | Defines the IP match value for Classless Inter-Domain Routing (CIDR) matching. |
| [OH_TrafficFilter_IPRange](capi-trafficfilter-oh-trafficfilter-iprange.md) | OH_TrafficFilter_IPRange | Defines the IP match value for range matching. |
| [OH_TrafficFilter_IPMulti](capi-trafficfilter-oh-trafficfilter-ipmulti.md) | OH_TrafficFilter_IPMulti | Defines the IP match value for multi-IP matching. |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) | OH_TrafficFilter_IPMatch | Defines the IP match condition. |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) | OH_TrafficFilter_InterfaceMatch | Defines the interface match condition. |
| [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) | OH_TrafficFilter_PortRange | Defines the port matching value for range matching. |
| [OH_TrafficFilter_PortMulti](capi-trafficfilter-oh-trafficfilter-portmulti.md) | OH_TrafficFilter_PortMulti | Defines the port matching value for multi-port matching. |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) | OH_TrafficFilter_PortMatch | Defines the port match condition. |
| [OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) | OH_TrafficFilter_ConnectionInfo | Defines the connection information struct. It describes the five-tuple information of a network connection (source IP, destination IP, source port, destination port, and protocol type), which is used to query the process that initiates the connection. Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_ConnectionInfo)**. Binary compatibility rule (ABI, that is, Application Binary Interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current interface, the interface returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. |
| [OH_TrafficFilter_ProcessInfo](capi-trafficfilter-oh-trafficfilter-processinfo.md) | OH_TrafficFilter_ProcessInfo | Defines the process information struct. Stores the process information returned by [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess). Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct to zero (for example, using memset), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_ProcessInfo)**. Binary compatibility rule (ABI, that is, Application Binary Interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system uses [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to determine which output fields can be safely written. Only fields fully covered by [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) are written by the system. If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required to read the [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) field itself, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. Output validity rule: When [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess) returns [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode), the fields covered by [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) contain valid output values. When the API returns an error, the caller must not rely on the values of output fields other than [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). |
| [OH_TrafficFilter_RedirectRule](capi-trafficfilter-oh-trafficfilter-redirectrule.md) | OH_TrafficFilter_RedirectRule | Defines the traffic redirection rule. Defines a TCP traffic redirection rule to redirect matching traffic to a specified proxy server. Initialization rule: Before calling [OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, usually **sizeof(OH_TrafficFilter_RedirectRule)**. Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. Failure rule: If [OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule) returns an error, it is not guaranteed that the rule has been added or taken effect. The caller should check the return value before assuming that the rule has taken effect. |
| [OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md) | OH_TrafficFilter_PacketDesc | Defines the packet descriptor. |
| [OH_TrafficFilter_Config](capi-trafficfilter-oh-trafficfilter-config.md) | OH_TrafficFilter_Config | Defines the configuration struct of an NFQueue (a packet queuing channel in the Netfilter framework). Initialization rule: Before calling [OH_TrafficFilter_CreatePacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_Config)**. Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) | OH_TrafficFilter_MACMatch | Defines the MAC address matching condition. |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) | OH_TrafficFilter_TCPFlagsMatch | Defines the TCP flag matching condition. It is valid only for the TCP protocol. |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) | OH_TrafficFilter_ConntrackMatch | Defines the connection tracking match condition. |
| [OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md) | OH_TrafficFilter_FilterRule | Defines a packet filtering rule. The conditions within a single **OH_TrafficFilter_FilterRule** struct are in a logical AND relationship, and multiple rules added to the same **OH_TrafficFilter_PacketController** are in a logical OR relationship. Initialization rule: Before calling [OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, usually **sizeof(OH_TrafficFilter_FilterRule)**. Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. Failure rule: If [OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule) returns an error, it is not guaranteed that the rule has been added or taken effect. The caller should check the return value before assuming that the rule has taken effect. |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md) | OH_TrafficFilter_Redirector | Defines a traffic redirector. |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) | OH_TrafficFilter_PacketController | Defines the packet controller. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_TrafficFilter_ErrCode](#oh_trafficfilter_errcode) | OH_TrafficFilter_ErrCode | Defines the error codes for traffic filtering and redirection. |
| [OH_TrafficFilter_IPMatchType](#oh_trafficfilter_ipmatchtype) | OH_TrafficFilter_IPMatchType | Defines an IP match type. |
| [OH_TrafficFilter_IPFamily](#oh_trafficfilter_ipfamily) | OH_TrafficFilter_IPFamily | Defines an IP address family. |
| [OH_TrafficFilter_PortMatchType](#oh_trafficfilter_portmatchtype) | OH_TrafficFilter_PortMatchType | Defines a port match type. |
| [OH_TrafficFilter_HookPoint](#oh_trafficfilter_hookpoint) | OH_TrafficFilter_HookPoint | Enumerates the hook points, specifying where the rule takes effect in the network protocol stack. As packets pass through the kernel network protocol stack, hook points are triggered at different stages, and the rule intercepts packets at the corresponding hook points. For example, the INPUT chain processes packets entering the local device, and the OUTPUT chain processes packets sent from the local device. |
| [OH_TrafficFilter_PacketDecision](#oh_trafficfilter_packetdecision) | OH_TrafficFilter_PacketDecision | Enumerates the packet processing decision types. |
| [OH_TrafficFilter_PacketCopyMode](#oh_trafficfilter_packetcopymode) | OH_TrafficFilter_PacketCopyMode | Enumerates the packet copy modes. |

### Macros

| Name | Description |
| -- | -- |
| OH_TRAFFICFILTER_IP_ADDRLEN       16 | Maximum length of the IP address byte array (compatible with both IPv4 and IPv6).<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT  16 | Maximum number of IP addresses supported for multi–IP address matching.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT 64 | Maximum number of ports supported for multi-port matching.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_META   0 | NFQueue packet copy mode: copies only metadata.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_PACKET 0xFFFF | NFQueue packet copy mode: copies the entire packet.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_COPY_LEN    0xFFFF | Default length of the copied NFQueue packet, in bytes. If the value is **0xFFFF**, the entire packet is copied; if a smaller value, such as **128**, is used, only the packet header is copied.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_QUEUE_MAXLEN  1024 | Default maximum length of the NFQueue queue (number of packets).<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN  0x1 | NFQueue queue flag: FAIL-OPEN mode. When a user-mode process crashes, the kernel automatically allows packets to pass to avoid network interruption.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_MAC_ADDRSTRLEN       18 | Maximum length of a MAC address string (in the XX:XX:XX:XX:XX:XX format).<br>**Since**: 26.0.1 |
| OH_TRAFFICFILTER_MIN_PRIORITY        1 | Minimum priority.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_MAX_PRIORITY        10000 | Maximum priority.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_MIN_GROUP_ID        1 | Minimum group ID value.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_MAX_GROUP_ID        65535 | Maximum group ID value.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_IFNAMSIZ            32 | Maximum length of the network interface name.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ANY           0 | Protocol constant: any protocol.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_PROTO_TCP           6 | Protocol constant: TCP.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_PROTO_UDP           17 | Protocol constant: UDP.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ICMP          1 | Protocol constant: ICMP.<br>**Since**: 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ICMPV6        58 | Protocol constant: ICMPv6.<br>**Since**: 26.0.0 |

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef OH_TrafficFilter_PacketDecision (\*OH_TrafficFilter_PacketCallback)(const OH_TrafficFilter_PacketDesc* packet, void* userData)](#oh_trafficfilter_packetcallback) | OH_TrafficFilter_PacketCallback | Packet callback function type |

## Enum type description

### OH_TrafficFilter_ErrCode

```c
enum OH_TrafficFilter_ErrCode
```

**Description**

Defines the error codes for traffic filtering and redirection.

<!--Device-enum OH_TrafficFilter_ErrCode--><!--Device-enum OH_TrafficFilter_ErrCode-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_OK = 0 | Operation succeeded.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_OK = 0--><!--Device-OH_TRAFFICFILTER_OK = 0-End--> |
| OH_TRAFFICFILTER_E_BASE = 29410000 | Base value for the error code.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_E_BASE = 29410000--><!--Device-OH_TRAFFICFILTER_E_BASE = 29410000-End--> |
| OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201 | Permission denied.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201--><!--Device-OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201-End--> |
| OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101) | Parameter error (invalid priority, IP address, port, or group ID).<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101)--><!--Device-OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101)-End--> |
| OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102) | Resource not found (rule, target, process, or group ID not found).<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102)--><!--Device-OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102)-End--> |
| OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103) | Too many rules.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103)--><!--Device-OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103)-End--> |
| OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104) | Group ID already in use.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104)--><!--Device-OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104)-End--> |
| OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105) | NFQueue error (initialization failed or no available queue).<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105)--><!--Device-OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105)-End--> |

### OH_TrafficFilter_IPMatchType

```c
enum OH_TrafficFilter_IPMatchType
```

**Description**

Defines an IP match type.

<!--Device-enum OH_TrafficFilter_IPMatchType--><!--Device-enum OH_TrafficFilter_IPMatchType-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_IP_MATCH_ANY = 0 | Any IP address.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_MATCH_ANY = 0--><!--Device-OH_TRAFFICFILTER_IP_MATCH_ANY = 0-End--> |
| OH_TRAFFICFILTER_IP_MATCH_SINGLE | Single IP address.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_MATCH_SINGLE--><!--Device-OH_TRAFFICFILTER_IP_MATCH_SINGLE-End--> |
| OH_TRAFFICFILTER_IP_MATCH_CIDR | CIDR (for example, **192.168.1.0/24**, which matches all IP addresses in the subnet).<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_MATCH_CIDR--><!--Device-OH_TRAFFICFILTER_IP_MATCH_CIDR-End--> |
| OH_TRAFFICFILTER_IP_MATCH_RANGE | IP address range.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_MATCH_RANGE--><!--Device-OH_TRAFFICFILTER_IP_MATCH_RANGE-End--> |
| OH_TRAFFICFILTER_IP_MATCH_MULTI | Multiple IP addresses.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_MATCH_MULTI--><!--Device-OH_TRAFFICFILTER_IP_MATCH_MULTI-End--> |

### OH_TrafficFilter_IPFamily

```c
enum OH_TrafficFilter_IPFamily
```

**Description**

Defines an IP address family.

<!--Device-enum OH_TrafficFilter_IPFamily--><!--Device-enum OH_TrafficFilter_IPFamily-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0 | Unspecified IP address family.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0--><!--Device-OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0-End--> |
| OH_TRAFFICFILTER_IP_FAMILY_V4 = 1 | IPv4 address family.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_FAMILY_V4 = 1--><!--Device-OH_TRAFFICFILTER_IP_FAMILY_V4 = 1-End--> |
| OH_TRAFFICFILTER_IP_FAMILY_V6 = 2 | IPv6 address family.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_IP_FAMILY_V6 = 2--><!--Device-OH_TRAFFICFILTER_IP_FAMILY_V6 = 2-End--> |

### OH_TrafficFilter_PortMatchType

```c
enum OH_TrafficFilter_PortMatchType
```

**Description**

Defines a port match type.

<!--Device-enum OH_TrafficFilter_PortMatchType--><!--Device-enum OH_TrafficFilter_PortMatchType-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_PORT_MATCH_ANY = 0 | Any port.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_PORT_MATCH_ANY = 0--><!--Device-OH_TRAFFICFILTER_PORT_MATCH_ANY = 0-End--> |
| OH_TRAFFICFILTER_PORT_MATCH_SINGLE | Single port.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_PORT_MATCH_SINGLE--><!--Device-OH_TRAFFICFILTER_PORT_MATCH_SINGLE-End--> |
| OH_TRAFFICFILTER_PORT_MATCH_RANGE | Port range.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_PORT_MATCH_RANGE--><!--Device-OH_TRAFFICFILTER_PORT_MATCH_RANGE-End--> |
| OH_TRAFFICFILTER_PORT_MATCH_MULTI | Multiple ports.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_PORT_MATCH_MULTI--><!--Device-OH_TRAFFICFILTER_PORT_MATCH_MULTI-End--> |

### OH_TrafficFilter_HookPoint

```c
enum OH_TrafficFilter_HookPoint
```

**Description**

Enumerates the hook points, specifying where the rule takes effect in the network protocol stack. As packets pass through the kernel network protocol stack, hook points are triggered at different stages, and the rule intercepts packets at the corresponding hook points. For example, the INPUT chain processes packets entering the local device, and the OUTPUT chain processes packets sent from the local device.

<!--Device-enum OH_TrafficFilter_HookPoint--><!--Device-enum OH_TrafficFilter_HookPoint-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_HOOK_INPUT = 0 | INPUT chain that processes packets received by the local host.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_HOOK_INPUT = 0--><!--Device-OH_TRAFFICFILTER_HOOK_INPUT = 0-End--> |
| OH_TRAFFICFILTER_HOOK_OUTPUT | OUTPUT chain that processes packets sent from the local host.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_HOOK_OUTPUT--><!--Device-OH_TRAFFICFILTER_HOOK_OUTPUT-End--> |
| OH_TRAFFICFILTER_HOOK_FORWARD | FORWARD chain that processes packets forwarded by the local host.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_HOOK_FORWARD--><!--Device-OH_TRAFFICFILTER_HOOK_FORWARD-End--> |
| OH_TRAFFICFILTER_HOOK_PREROUTING | PREROUTING chain that processes packets that have arrived at the NIC but not been routed.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_HOOK_PREROUTING--><!--Device-OH_TRAFFICFILTER_HOOK_PREROUTING-End--> |
| OH_TRAFFICFILTER_HOOK_POSTROUTING | POSTROUTING chain that processes packets about to be sent from the NIC.<br>**Since**: 26.0.0<br><!--Device-OH_TRAFFICFILTER_HOOK_POSTROUTING--><!--Device-OH_TRAFFICFILTER_HOOK_POSTROUTING-End--> |

### OH_TrafficFilter_PacketDecision

```c
enum OH_TrafficFilter_PacketDecision
```

**Description**

Enumerates the packet processing decision types.

<!--Device-enum OH_TrafficFilter_PacketDecision--><!--Device-enum OH_TrafficFilter_PacketDecision-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_DECISION_ACCEPT = 0 | Accepts the packet.<br>**Since**: 26.0.1<br><!--Device-OH_TRAFFICFILTER_DECISION_ACCEPT = 0--><!--Device-OH_TRAFFICFILTER_DECISION_ACCEPT = 0-End--> |
| OH_TRAFFICFILTER_DECISION_DROP | Drops the packet.<br>**Since**: 26.0.1<br><!--Device-OH_TRAFFICFILTER_DECISION_DROP--><!--Device-OH_TRAFFICFILTER_DECISION_DROP-End--> |

### OH_TrafficFilter_PacketCopyMode

```c
enum OH_TrafficFilter_PacketCopyMode
```

**Description**

Enumerates the packet copy modes.

<!--Device-enum OH_TrafficFilter_PacketCopyMode--><!--Device-enum OH_TrafficFilter_PacketCopyMode-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

| Enum item | Description |
| -- | -- |
| OH_TRAFFICFILTER_COPY_MODE_META = 0 | Copies only the metadata (without copying the packet data).<br>**Since**: 26.0.1<br><!--Device-OH_TRAFFICFILTER_COPY_MODE_META = 0--><!--Device-OH_TRAFFICFILTER_COPY_MODE_META = 0-End--> |
| OH_TRAFFICFILTER_COPY_MODE_HEADER = 1 | Copies only the packet header (specified by **packetCopyLen**).<br>**Since**: 26.0.1<br><!--Device-OH_TRAFFICFILTER_COPY_MODE_HEADER = 1--><!--Device-OH_TRAFFICFILTER_COPY_MODE_HEADER = 1-End--> |
| OH_TRAFFICFILTER_COPY_MODE_FULL = 2 | Copies the entire packet.<br>**Since**: 26.0.1<br><!--Device-OH_TRAFFICFILTER_COPY_MODE_FULL = 2--><!--Device-OH_TRAFFICFILTER_COPY_MODE_FULL = 2-End--> |
| OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3 | Copies the packet of the specified maximum length.<br>**Since**: 26.0.1<br><!--Device-OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3--><!--Device-OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3-End--> |


## Function description

### OH_TrafficFilter_PacketCallback()

```c
typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(const OH_TrafficFilter_PacketDesc* packet, void* userData)
```

**Description**

Packet callback function type

<!--Device-typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(const OH_TrafficFilter_PacketDesc* packet, void* userData)--><!--Device-typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(const OH_TrafficFilter_PacketDesc* packet, void* userData)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md)* packet | Packet descriptor |
| void* userData | User data |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_TrafficFilter_PacketDecision](capi-net-trafficfilter-type-h.md#oh_trafficfilter_packetdecision) | Packet decision (ACCEPT or DROP) |


