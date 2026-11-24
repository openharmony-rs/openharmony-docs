# NetConn_HttpProxy

```c
typedef struct NetConn_HttpProxy {...} NetConn_HttpProxy
```

## Overview

Defines the proxy configuration.

<!--Device-struct NetConn_HttpProxy {...}--><!--Device-struct NetConn_HttpProxy {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char host[NETCONN_MAX_STR_LEN] | Host name<br><!--Device-char host[NETCONN_MAX_STR_LEN]--><!--Device-char host[NETCONN_MAX_STR_LEN]-End--> |
| char exclusionList[NETCONN_MAX_EXCLUSION_SIZE][NETCONN_MAX_STR_LEN] | Exclusion list of proxy servers<br><!--Device-char exclusionList[NETCONN_MAX_EXCLUSION_SIZE][NETCONN_MAX_STR_LEN]--><!--Device-char exclusionList[NETCONN_MAX_EXCLUSION_SIZE][NETCONN_MAX_STR_LEN]-End--> |
| int32_t exclusionListSize | Actual size of the exclusion list.<br><!--Device-int32_t exclusionListSize--><!--Device-int32_t exclusionListSize-End--> |
| uint16_t port | Port number.<br><!--Device-uint16_t port--><!--Device-uint16_t port-End--> |


