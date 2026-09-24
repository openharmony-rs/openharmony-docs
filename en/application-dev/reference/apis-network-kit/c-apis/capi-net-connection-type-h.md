# net_connection_type.h

## Overview

Defines the data structures for the C APIs of the network connection module.

**Library**: libnet_connection.so

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-netconnection.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) | NetConn_NetHandle | Defines network handles for network IDs. |
| [NetConn_NetCapabilities](capi-netconnection-netconn-netcapabilities.md) | NetConn_NetCapabilities | Defines network capability sets. |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) | NetConn_NetAddr | Defines network addresses. |
| [NetConn_Route](capi-netconnection-netconn-route.md) | NetConn_Route | Defines the route configuration. |
| [NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) | NetConn_HttpProxy | Defines the proxy configuration. |
| [NetConn_ConnectionProperties](capi-netconnection-netconn-connectionproperties.md) | NetConn_ConnectionProperties | Defines the network connection properties. |
| [NetConn_NetHandleList](capi-netconnection-netconn-nethandlelist.md) | NetConn_NetHandleList | Defines the network list. |
| [NetConn_NetSpecifier](capi-netconnection-netconn-netspecifier.md) | NetConn_NetSpecifier | Defines network feature sets. |
| [NetConn_NetConnCallback](capi-netconnection-netconn-netconncallback.md) | NetConn_NetConnCallback | Defines a struct for the network status listener callback collection. All callback events must be registered; those not requiring attention can be set to empty. |
| [NetConn_ProbeResultInfo](capi-netconnection-netconn-proberesultinfo.md) | NetConn_ProbeResultInfo | Defines the probe result. |
| [NetConn_TraceRouteOption](capi-netconnection-netconn-tracerouteoption.md) | NetConn_TraceRouteOption | Defines the network trace route options. |
| [NetConn_TraceRouteInfo](capi-netconnection-netconn-tracerouteinfo.md) | NetConn_TraceRouteInfo | Defines the trace route information. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NetConn_NetCap](#netconn_netcap) | NetConn_NetCap | Enumerates the network capabilities. |
| [NetConn_NetBearerType](#netconn_netbearertype) | NetConn_NetBearerType | Enumerates the network carrier types. |
| [NetConn_ErrorCode](#netconn_errorcode) | NetConn_ErrorCode | Enumerates network connection error codes. |
| [NetConn_PacketsType](#netconn_packetstype) | NetConn_PacketsType | Enumerates trace route packet types. |

### Macro

| Name | Description |
| -- | -- |
| NETCONN_MAX_NET_SIZE 32 | Length of the netHandles array in the member variable of NetConn_NetHandleList.<br>**Since**: 11 |
| NETCONN_MAX_BEARER_TYPE_SIZE 32 | Length of the bearerTypes array in the NetConn_NetCapabilities member variable.<br>**Since**: 11 |
| NETCONN_MAX_CAP_SIZE 32 | Length of the netCaps array in the NetConn_NetCapabilities member variable.<br>**Since**: 11 |
| NETCONN_MAX_ADDR_SIZE 32 | Length of the netAddrlist and dnsList arrays in the NetConn_ConnectionProperties member variable.<br>**Since**: 11 |
| NETCONN_MAX_ROUTE_SIZE 64 | Length of the routeList array in the NetConn_ConnectionProperties member variable.<br>**Since**: 11 |
| NETCONN_MAX_EXCLUSION_SIZE 256 | Length of the exclusionList array in the NetConn_HttpProxy member variable.<br>**Since**: 11 |
| NETCONN_MAX_STR_LEN 256 | Length of the host array of the NetConn_HttpProxy member variable.<br>**Since**: 11 |
| NETCONN_MAX_RTT_NUM 4 | Length of the rtts array in the NetConn_ProbeResultlnfo member variable.<br>**Since**: 20 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef int (\*OH_NetConn_CustomDnsResolver)(const char *host, const char *serv, const struct addrinfo *hint, struct addrinfo **res)](#oh_netconn_customdnsresolver) | OH_NetConn_CustomDnsResolver | Defines the pointer to the custom DNS resolver. |
| [typedef void (\*OH_NetConn_AppHttpProxyChange)(NetConn_HttpProxy *proxy)](#oh_netconn_apphttpproxychange) | OH_NetConn_AppHttpProxyChange | Defines the callback invoked when the HTTP proxy information of the application changes. |
| [typedef void (\*OH_NetConn_GlobalHttpProxyRefreshCallback)(int32_t result, const NetConn_HttpProxy *proxy, void *userContext)](#oh_netconn_globalhttpproxyrefreshcallback) | OH_NetConn_GlobalHttpProxyRefreshCallback | Defines the one-shot callback used to receive the global HTTP proxy re-authentication result.<br> This callback is invoked at most once for each successful call to OH_NetConn_RefreshGlobalHttpProxyWithCallback. |
| [typedef void (\*OH_NetConn_NetworkAvailable)(NetConn_NetHandle *netHandle)](#oh_netconn_networkavailable) | OH_NetConn_NetworkAvailable | Defines the callback invoked when the network is available. |
| [typedef void (\*OH_NetConn_NetCapabilitiesChange)(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities)](#oh_netconn_netcapabilitieschange) | OH_NetConn_NetCapabilitiesChange | Defines the callback invoked when the network capabilities change. |
| [typedef void (\*OH_NetConn_NetConnectionPropertiesChange)(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *connConnetionProperties)](#oh_netconn_netconnectionpropertieschange) | OH_NetConn_NetConnectionPropertiesChange | Defines the callback invoked when network connection properties change. |
| [typedef void (\*OH_NetConn_NetLost)(NetConn_NetHandle *netHandle)](#oh_netconn_netlost) | OH_NetConn_NetLost | Defines the callback invoked when the network is disconnected. |
| [typedef void (\*OH_NetConn_NetUnavailable)(void)](#oh_netconn_netunavailable) | OH_NetConn_NetUnavailable | Defines the callback invoked when the network is unavailable. This callback is triggered when the network is not activated within the specified timeout interval. If the timeout interval is not set, this callback is not triggered. |
| [typedef void (\*OH_NetConn_NetBlockStatusChange)(NetConn_NetHandle *netHandle, bool blocked)](#oh_netconn_netblockstatuschange) | OH_NetConn_NetBlockStatusChange | Defines the callback invoked when the network blocking status changes. |

### Variable

| Name | Description |
| -- | -- |
| int (*OH_NetConn_CustomDnsResolver)(const char *host, const char *serv, const struct addrinfo *hint, struct addrinfo **res) | Defines the pointer to the custom DNS resolver.<br>**Since**: 11 |
| void (*OH_NetConn_AppHttpProxyChange)(NetConn_HttpProxy *proxy) | Defines the callback invoked when the HTTP proxy information of the application changes.<br>**Since**: 12 |
| void (*OH_NetConn_GlobalHttpProxyRefreshCallback)( int32_t result, const NetConn_HttpProxy *proxy, void *userContext) | Defines the one-shot callback used to receive the global HTTP proxy re-authentication result.<br> This callback is invoked at most once for each successful call to OH_NetConn_RefreshGlobalHttpProxyWithCallback.<br>**Since**: 26.0.0 |
| void (*OH_NetConn_NetworkAvailable)(NetConn_NetHandle *netHandle) | Defines the callback invoked when the network is available.<br>**Since**: 12 |
| void (*OH_NetConn_NetCapabilitiesChange)(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities) | Defines the callback invoked when the network capabilities change.<br>**Since**: 12 |
| void (*OH_NetConn_NetConnectionPropertiesChange)(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *connConnetionProperties) | Defines the callback invoked when network connection properties change.<br>**Since**: 12 |
| void (*OH_NetConn_NetLost)(NetConn_NetHandle *netHandle) | Defines the callback invoked when the network is disconnected.<br>**Since**: 12 |
| void (*OH_NetConn_NetUnavailable)(void) | Defines the callback invoked when the network is unavailable. This callback is triggered when the network is not activated within the specified timeout interval. If the timeout interval is not set, this callback is not triggered.<br>**Since**: 12 |
| void (*OH_NetConn_NetBlockStatusChange)(NetConn_NetHandle *netHandle, bool blocked) | Defines the callback invoked when the network blocking status changes.<br>**Since**: 12 |

## Enum type description

### NetConn_NetCap

```c
enum NetConn_NetCap
```

**Description**

Enumerates the network capabilities.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| NETCONN_NET_CAPABILITY_MMS = 0 | MMS. |
| NETCONN_NET_CAPABILITY_NOT_METERED = 11 | Non-metered network. |
| NETCONN_NET_CAPABILITY_INTERNET = 12 | Internet. |
| NETCONN_NET_CAPABILITY_NOT_VPN = 15 | Non-VPN. |
| NETCONN_NET_CAPABILITY_VALIDATED = 16 | Verified. |
| NETCONN_NET_CAPABILITY_PORTAL = 17 |  |
| NETCONN_NET_CAPABILITY_CHECKING_CONNECTIVITY = 31 |  |

### NetConn_NetBearerType

```c
enum NetConn_NetBearerType
```

**Description**

Enumerates the network carrier types.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| NETCONN_BEARER_CELLULAR = 0 | Cellular network. |
| NETCONN_BEARER_WIFI = 1 | Wi-Fi. |
| NETCONN_BEARER_BLUETOOTH = 2 |  |
| NETCONN_BEARER_ETHERNET = 3 | Ethernet. |
| NETCONN_BEARER_VPN = 4 |  |

### NetConn_ErrorCode

```c
enum NetConn_ErrorCode
```

**Description**

Enumerates network connection error codes.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 15

| Enum item | Description |
| -- | -- |
| NETCONN_SUCCESS = 0 | Success. |
| NETCONN_PERMISSION_DENIED = 201 | Missing permissions. |
| NETCONN_PARAMETER_ERROR = 401 | Invalid parameter. |
| NETCONN_OPERATION_FAILED = 2100002 | Service connection failure. |
| NETCONN_INTERNAL_ERROR = 2100003 | Internal error.1. Memory-related error, for example, insufficient memory, memory data copy failure, or memory request failure.2. Null pointer, for example, access to a released memory pointer. |

### NetConn_PacketsType

```c
enum NetConn_PacketsType
```

**Description**

Enumerates trace route packet types.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| NETCONN_PACKETS_ICMP = 0 | Internet Control Message Protocol. |
| NETCONN_PACKETS_UDP = 1 | User Datagram Protocol. |


## Function description

### OH_NetConn_CustomDnsResolver()

```c
typedef int (*OH_NetConn_CustomDnsResolver)(const char *host, const char *serv, const struct addrinfo *hint, struct addrinfo **res)
```

**Description**

Defines the pointer to the custom DNS resolver.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char \*host | Host name. |
| const char \*serv | Service name. |
| const struct addrinfo \*hint | Pointer to the addrinfo structure. |
| struct addrinfo \*\*res | DNS query result, which is in the format of linked lists. |

### OH_NetConn_AppHttpProxyChange()

```c
typedef void (*OH_NetConn_AppHttpProxyChange)(NetConn_HttpProxy *proxy)
```

**Description**

Defines the callback invoked when the HTTP proxy information of the application changes.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) \*proxy | Proxy configuration information (probably a null pointer). |

### OH_NetConn_GlobalHttpProxyRefreshCallback()

```c
typedef void (*OH_NetConn_GlobalHttpProxyRefreshCallback)(int32_t result, const NetConn_HttpProxy *proxy, void *userContext)
```

**Description**

Defines the one-shot callback used to receive the global HTTP proxy re-authentication result.<br> This callback is invoked at most once for each successful call to OH_NetConn_RefreshGlobalHttpProxyWithCallback.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t result | The re-authentication result. 0 indicates success. Other values indicate failure. |
| [const NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) \*proxy | The refreshed global HTTP proxy information when result is 0. If re-authentication fails, proxy is NULL.<br> The proxy object is owned by the system and is valid only during this callback invocation. The caller must not free or modify it. If the caller needs to use the proxy information after the callback returns, the caller must make a deep copy. |
| void \*userContext | The user-defined data passed to OH_NetConn_RefreshGlobalHttpProxyWithCallback. The system does not access, copy, or release it. |

### OH_NetConn_NetworkAvailable()

```c
typedef void (*OH_NetConn_NetworkAvailable)(NetConn_NetHandle *netHandle)
```

**Description**

Defines the callback invoked when the network is available.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | Network handle. |

### OH_NetConn_NetCapabilitiesChange()

```c
typedef void (*OH_NetConn_NetCapabilitiesChange)(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities)
```

**Description**

Defines the callback invoked when the network capabilities change.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | Network handle. |
| [NetConn_NetCapabilities](capi-netconnection-netconn-netcapabilities.md) \*netCapabilities | Network capability set. |

### OH_NetConn_NetConnectionPropertiesChange()

```c
typedef void (*OH_NetConn_NetConnectionPropertiesChange)(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *connConnetionProperties)
```

**Description**

Defines the callback invoked when network connection properties change.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | Network handle. |
| [NetConn_ConnectionProperties](capi-netconnection-netconn-connectionproperties.md) \*connConnetionProperties | Network connection properties. |

### OH_NetConn_NetLost()

```c
typedef void (*OH_NetConn_NetLost)(NetConn_NetHandle *netHandle)
```

**Description**

Defines the callback invoked when the network is disconnected.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | Network handle. |

### OH_NetConn_NetUnavailable()

```c
typedef void (*OH_NetConn_NetUnavailable)(void)
```

**Description**

Defines the callback invoked when the network is unavailable. This callback is triggered when the network is not activated within the specified timeout interval. If the timeout interval is not set, this callback is not triggered.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

### OH_NetConn_NetBlockStatusChange()

```c
typedef void (*OH_NetConn_NetBlockStatusChange)(NetConn_NetHandle *netHandle, bool blocked)
```

**Description**

Defines the callback invoked when the network blocking status changes.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | Network handle. |
| bool blocked | Whether the network is blocked. The value true indicates that the network is blocked, and the value false indicates the opposite. |


