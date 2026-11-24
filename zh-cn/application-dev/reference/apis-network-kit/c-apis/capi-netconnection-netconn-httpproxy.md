# NetConn_HttpProxy

```c
typedef struct NetConn_HttpProxy {...} NetConn_HttpProxy
```

## 概述

代理配置信息。

<!--Device-struct NetConn_HttpProxy {...}--><!--Device-struct NetConn_HttpProxy {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**起始版本：** 11

**相关模块：** [NetConnection](capi-network-kit-netconnection.md)

**所在头文件：** [net_connection_type.h](capi-net-connection-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char host[NETCONN_MAX_STR_LEN] | Host name<br><!--Device-char host[NETCONN_MAX_STR_LEN]--><!--Device-char host[NETCONN_MAX_STR_LEN]-End--> |
| char exclusionList[NETCONN_MAX_EXCLUSION_SIZE][NETCONN_MAX_STR_LEN] | Exclusion list of proxy servers<br><!--Device-char exclusionList[NETCONN_MAX_EXCLUSION_SIZE][NETCONN_MAX_STR_LEN]--><!--Device-char exclusionList[NETCONN_MAX_EXCLUSION_SIZE][NETCONN_MAX_STR_LEN]-End--> |
| int32_t exclusionListSize | 排除列表的实际大小。<br><!--Device-int32_t exclusionListSize--><!--Device-int32_t exclusionListSize-End--> |
| uint16_t port | 端口号。<br><!--Device-uint16_t port--><!--Device-uint16_t port-End--> |


