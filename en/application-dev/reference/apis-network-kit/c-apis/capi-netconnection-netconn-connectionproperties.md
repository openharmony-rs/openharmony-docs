# NetConn_ConnectionProperties

```c
typedef struct NetConn_ConnectionProperties {...} NetConn_ConnectionProperties
```

## Overview

Defines the network connection properties.

<!--Device-struct NetConn_ConnectionProperties {...}--><!--Device-struct NetConn_ConnectionProperties {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char ifaceName[NETCONN_MAX_STR_LEN] | Network interface name<br><!--Device-char ifaceName[NETCONN_MAX_STR_LEN]--><!--Device-char ifaceName[NETCONN_MAX_STR_LEN]-End--> |
| char domain[NETCONN_MAX_STR_LEN] | Domain name of the network connection<br><!--Device-char domain[NETCONN_MAX_STR_LEN]--><!--Device-char domain[NETCONN_MAX_STR_LEN]-End--> |
| char tcpBufferSizes[NETCONN_MAX_STR_LEN] | TCP buffer size<br><!--Device-char tcpBufferSizes[NETCONN_MAX_STR_LEN]--><!--Device-char tcpBufferSizes[NETCONN_MAX_STR_LEN]-End--> |
| uint16_t mtu | Maximum transmission unit.<br><!--Device-uint16_t mtu--><!--Device-uint16_t mtu-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) netAddrList[NETCONN_MAX_ADDR_SIZE] | Address list<br><!--Device-NetConn_NetAddr netAddrList[NETCONN_MAX_ADDR_SIZE]--><!--Device-NetConn_NetAddr netAddrList[NETCONN_MAX_ADDR_SIZE]-End--> |
| int32_t netAddrListSize | Actual size of the address list.<br><!--Device-int32_t netAddrListSize--><!--Device-int32_t netAddrListSize-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) dnsList[NETCONN_MAX_ADDR_SIZE] | DNS list<br><!--Device-NetConn_NetAddr dnsList[NETCONN_MAX_ADDR_SIZE]--><!--Device-NetConn_NetAddr dnsList[NETCONN_MAX_ADDR_SIZE]-End--> |
| int32_t dnsListSize | Actual size of the DNS list.<br><!--Device-int32_t dnsListSize--><!--Device-int32_t dnsListSize-End--> |
| [NetConn_Route](capi-netconnection-netconn-route.md) routeList[NETCONN_MAX_ROUTE_SIZE] | Route list<br><!--Device-NetConn_Route routeList[NETCONN_MAX_ROUTE_SIZE]--><!--Device-NetConn_Route routeList[NETCONN_MAX_ROUTE_SIZE]-End--> |
| int32_t routeListSize | Actual size of the route list.<br><!--Device-int32_t routeListSize--><!--Device-int32_t routeListSize-End--> |
| [NetConn_HttpProxy](capi-netconnection-netconn-httpproxy.md) httpProxy | HTTP proxy information.<br><!--Device-NetConn_HttpProxy httpProxy--><!--Device-NetConn_HttpProxy httpProxy-End--> |


