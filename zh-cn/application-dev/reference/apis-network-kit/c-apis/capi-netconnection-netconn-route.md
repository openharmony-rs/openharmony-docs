# NetConn_Route

```c
typedef struct NetConn_Route {...} NetConn_Route
```

## 概述

路由配置信息。

<!--Device-struct NetConn_Route {...}--><!--Device-struct NetConn_Route {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**起始版本：** 11

**相关模块：** [NetConnection](capi-network-kit-netconnection.md)

**所在头文件：** [net_connection_type.h](capi-net-connection-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char iface[NETCONN_MAX_STR_LEN] | 网络接口。<br><!--Device-char iface[NETCONN_MAX_STR_LEN]--><!--Device-char iface[NETCONN_MAX_STR_LEN]-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) destination | 目标地址<br><!--Device-NetConn_NetAddr destination--><!--Device-NetConn_NetAddr destination-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) gateway | 网关地址<br><!--Device-NetConn_NetAddr gateway--><!--Device-NetConn_NetAddr gateway-End--> |
| int32_t hasGateway | 是否存在网关<br><!--Device-int32_t hasGateway--><!--Device-int32_t hasGateway-End--> |
| int32_t isDefaultRoute | 是否是默认路由<br><!--Device-int32_t isDefaultRoute--><!--Device-int32_t isDefaultRoute-End--> |


