# net_connection_type.h

## 概述

定义网络管理数据网络连接模块的C接口数据结构。

**库：** libnet_connection.so

**系统能力：** SystemCapability.Communication.NetManager.Core

**起始版本：** 11

**相关模块：** [NetConnection](capi-netconnection.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) | 存放网络ID。 |
| [NetConn_NetCapabilities](capi-netconnection-netconn-netcapabilities.md) | 网络能力集。 |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) | 网络地址。 |
| [NetConn_Route](capi-netconnection-netconn-route.md) | 路由配置信息。 |
| [NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) | 代理配置信息。 |
| [NetConn_ConnectionProperties](capi-netconnection-netconn-connectionproperties.md) | 网络连接信息。 |
| [NetConn_NetHandleList](capi-netconnection-netconn-nethandlelist.md) | 网络列表。 |
| [NetConn_NetSpecifier](capi-netconnection-netconn-netspecifier.md) | 网络的特征集。 |
| [NetConn_NetConnCallback](capi-netconnection-netconn-netconncallback.md) | 网络状态监听回调集合，所有回调事件需全部注册，无需关注的回调可以设为空实现。 |
| [NetConn_ProbeResultInfo](capi-netconnection-netconn-proberesultinfo.md) | 定义探测结果信息。 |
| [NetConn_TraceRouteOption](capi-netconnection-netconn-tracerouteoption.md) | 定义网络跟踪路由选项。 |
| [NetConn_TraceRouteInfo](capi-netconnection-netconn-tracerouteinfo.md) | 定义跟踪路由信息。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| NETCONN_MAX_NET_SIZE 32 | NetConn_NetHandleList的成员变量netHandles数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_BEARER_TYPE_SIZE 32 | NetConn_NetCapabilities的成员变量bearerTypes数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_CAP_SIZE 32 | NetConn_NetCapabilities的成员变量netCaps数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_ADDR_SIZE 32 | NetConn_ConnectionProperties的成员变量netAddrList、dnsList数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_ROUTE_SIZE 64 | NetConn_ConnectionProperties的成员变量routeList数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_EXCLUSION_SIZE 256 | NetConn_HttpProxy的成员变量exclusionList数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_STR_LEN 256 | NetConn_HttpProxy的成员变量host数组的长度。<br>**起始版本：** 11 |
| NETCONN_MAX_RTT_NUM 4 | NetConn_ProbeResultInfo的成员变量rtt数组的长度。<br>**起始版本：** 20 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef int (\*OH_NetConn_CustomDnsResolver)(const char *host, const char *serv, const struct addrinfo *hint, struct addrinfo **res)](#oh_netconn_customdnsresolver) | OH_NetConn_CustomDnsResolver | 指向自定义DNS解析器的指针。 |
| [typedef void (\*OH_NetConn_AppHttpProxyChange)(NetConn_HttpProxy *proxy)](#oh_netconn_apphttpproxychange) | OH_NetConn_AppHttpProxyChange | 应用的http代理信息变化回调。 |
| [typedef void (\*OH_NetConn_GlobalHttpProxyRefreshCallback)(int32_t result, const NetConn_HttpProxy *proxy, void *userContext)](#oh_netconn_globalhttpproxyrefreshcallback) | OH_NetConn_GlobalHttpProxyRefreshCallback | 全局HTTP代理重新认证结果的回调。 |
| [typedef void (\*OH_NetConn_NetworkAvailable)(NetConn_NetHandle *netHandle)](#oh_netconn_networkavailable) | OH_NetConn_NetworkAvailable | 网络可用回调。 |
| [typedef void (\*OH_NetConn_NetCapabilitiesChange)(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities)](#oh_netconn_netcapabilitieschange) | OH_NetConn_NetCapabilitiesChange | 网络能力集变更回调。 |
| [typedef void (\*OH_NetConn_NetConnectionPropertiesChange)(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *connConnetionProperties)](#oh_netconn_netconnectionpropertieschange) | OH_NetConn_NetConnectionPropertiesChange | 网络连接属性变更回调。 |
| [typedef void (\*OH_NetConn_NetLost)(NetConn_NetHandle *netHandle)](#oh_netconn_netlost) | OH_NetConn_NetLost | 网络断开回调。 |
| [typedef void (\*OH_NetConn_NetUnavailable)(void)](#oh_netconn_netunavailable) | OH_NetConn_NetUnavailable | 网络不可用回调，在指定的超时时间内网络未激活时触发该回调，如果未设置超时时间则不会触发该回调。 |
| [typedef void (\*OH_NetConn_NetBlockStatusChange)(NetConn_NetHandle *netHandle, bool blocked)](#oh_netconn_netblockstatuschange) | OH_NetConn_NetBlockStatusChange | 网络阻塞状态变更回调。 |

## 函数说明

### OH_NetConn_CustomDnsResolver()

```c
typedef int (*OH_NetConn_CustomDnsResolver)(const char *host, const char *serv, const struct addrinfo *hint, struct addrinfo **res)
```

**描述**

指向自定义DNS解析器的指针。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char \*host | 要查询的主机名。 |
| const char \*serv | 服务名称。 |
| const struct addrinfo \*hint | 指向addrinfo结构的指针。 |
| struct addrinfo \*\*res | 存储DNS查询结果并以链表形式返回。 |

### OH_NetConn_AppHttpProxyChange()

```c
typedef void (*OH_NetConn_AppHttpProxyChange)(NetConn_HttpProxy *proxy)
```

**描述**

应用的http代理信息变化回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) \*proxy | 变化的代理配置信息，可能是空指针。 |

### OH_NetConn_GlobalHttpProxyRefreshCallback()

```c
typedef void (*OH_NetConn_GlobalHttpProxyRefreshCallback)(int32_t result, const NetConn_HttpProxy *proxy, void *userContext)
```

**描述**

全局HTTP代理重新认证结果的回调。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t result | 重新认证的结果。0表示成功，其他值表示失败。 |
| [const NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) \*proxy | The refreshed global HTTP proxy information when result is 0. If re-authenticationfails, proxy is NULL.<br>The proxy object is owned by the system and is valid only during this callbackinvocation. The caller must not free or modify it. If the caller needs to use theproxy information after the callback returns, the caller must make a deep copy. |
| void \*userContext | The user-defined data passed to OH_NetConn_RefreshGlobalHttpProxyWithCallback. The systemdoes not access, copy, or release it. |

### OH_NetConn_NetworkAvailable()

```c
typedef void (*OH_NetConn_NetworkAvailable)(NetConn_NetHandle *netHandle)
```

**描述**

网络可用回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | 网络句柄。 |

### OH_NetConn_NetCapabilitiesChange()

```c
typedef void (*OH_NetConn_NetCapabilitiesChange)(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities)
```

**描述**

网络能力集变更回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | 网络句柄。 |
| [NetConn_NetCapabilities](capi-netconnection-netconn-netcapabilities.md) \*netCapabilities | 网络能力集。 |

### OH_NetConn_NetConnectionPropertiesChange()

```c
typedef void (*OH_NetConn_NetConnectionPropertiesChange)(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *connConnetionProperties)
```

**描述**

网络连接属性变更回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | 网络句柄。 |
| [NetConn_ConnectionProperties](capi-netconnection-netconn-connectionproperties.md) \*connConnetionProperties | 网络连接属性。 |

### OH_NetConn_NetLost()

```c
typedef void (*OH_NetConn_NetLost)(NetConn_NetHandle *netHandle)
```

**描述**

网络断开回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | 网络句柄。 |

### OH_NetConn_NetUnavailable()

```c
typedef void (*OH_NetConn_NetUnavailable)(void)
```

**描述**

网络不可用回调，在指定的超时时间内网络未激活时触发该回调，如果未设置超时时间则不会触发该回调。

**起始版本：** 12

### OH_NetConn_NetBlockStatusChange()

```c
typedef void (*OH_NetConn_NetBlockStatusChange)(NetConn_NetHandle *netHandle, bool blocked)
```

**描述**

网络阻塞状态变更回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) \*netHandle | 网络句柄。 |
| bool blocked | 指示网络是否将被阻塞的标志。true表示网络被阻塞，false表示网络未被阻塞。 |


