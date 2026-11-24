# NetConn_ConnectionProperties

```c
typedef struct NetConn_ConnectionProperties {...} NetConn_ConnectionProperties
```

## 概述

网络连接信息。

<!--Device-struct NetConn_ConnectionProperties {...}--><!--Device-struct NetConn_ConnectionProperties {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**起始版本：** 11

**相关模块：** [NetConnection](capi-network-kit-netconnection.md)

**所在头文件：** [net_connection_type.h](capi-net-connection-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char ifaceName[NETCONN_MAX_STR_LEN] | 网络接口名称。<br><!--Device-char ifaceName[NETCONN_MAX_STR_LEN]--><!--Device-char ifaceName[NETCONN_MAX_STR_LEN]-End--> |
| char domain[NETCONN_MAX_STR_LEN] | 网络连接的域名。<br><!--Device-char domain[NETCONN_MAX_STR_LEN]--><!--Device-char domain[NETCONN_MAX_STR_LEN]-End--> |
| char tcpBufferSizes[NETCONN_MAX_STR_LEN] | TCP缓冲区大小。<br><!--Device-char tcpBufferSizes[NETCONN_MAX_STR_LEN]--><!--Device-char tcpBufferSizes[NETCONN_MAX_STR_LEN]-End--> |
| uint16_t mtu | MTU<br><!--Device-uint16_t mtu--><!--Device-uint16_t mtu-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) netAddrList[NETCONN_MAX_ADDR_SIZE] | 地址列表。<br><!--Device-NetConn_NetAddr netAddrList[NETCONN_MAX_ADDR_SIZE]--><!--Device-NetConn_NetAddr netAddrList[NETCONN_MAX_ADDR_SIZE]-End--> |
| int32_t netAddrListSize | 地址列表的实际size。<br><!--Device-int32_t netAddrListSize--><!--Device-int32_t netAddrListSize-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) dnsList[NETCONN_MAX_ADDR_SIZE] | DNS列表。<br><!--Device-NetConn_NetAddr dnsList[NETCONN_MAX_ADDR_SIZE]--><!--Device-NetConn_NetAddr dnsList[NETCONN_MAX_ADDR_SIZE]-End--> |
| int32_t dnsListSize | DNS列表的实际size。<br><!--Device-int32_t dnsListSize--><!--Device-int32_t dnsListSize-End--> |
| [NetConn_Route](capi-netconnection-netconn-route.md) routeList[NETCONN_MAX_ROUTE_SIZE] | 路由列表。<br><!--Device-NetConn_Route routeList[NETCONN_MAX_ROUTE_SIZE]--><!--Device-NetConn_Route routeList[NETCONN_MAX_ROUTE_SIZE]-End--> |
| int32_t routeListSize | 路由列表的实际大小。<br><!--Device-int32_t routeListSize--><!--Device-int32_t routeListSize-End--> |
| [NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) httpProxy | HTTP代理信息。<br><!--Device-NetConn_HttpProxy httpProxy--><!--Device-NetConn_HttpProxy httpProxy-End--> |


