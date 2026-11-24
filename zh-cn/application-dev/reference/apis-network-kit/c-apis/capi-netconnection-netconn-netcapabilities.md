# NetConn_NetCapabilities

```c
typedef struct NetConn_NetCapabilities {...} NetConn_NetCapabilities
```

## 概述

网络能力集。

<!--Device-struct NetConn_NetCapabilities {...}--><!--Device-struct NetConn_NetCapabilities {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**起始版本：** 11

**相关模块：** [NetConnection](capi-network-kit-netconnection.md)

**所在头文件：** [net_connection_type.h](capi-net-connection-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t linkUpBandwidthKbps | 上行带宽。<br><!--Device-uint32_t linkUpBandwidthKbps--><!--Device-uint32_t linkUpBandwidthKbps-End--> |
| uint32_t linkDownBandwidthKbps | 下行带宽。<br><!--Device-uint32_t linkDownBandwidthKbps--><!--Device-uint32_t linkDownBandwidthKbps-End--> |
| [NetConn_NetCap](capi-net-connection-type-h.md#netconn_netcap) netCaps[NETCONN_MAX_CAP_SIZE] | 网络能力列表。<br><!--Device-NetConn_NetCap netCaps[NETCONN_MAX_CAP_SIZE]--><!--Device-NetConn_NetCap netCaps[NETCONN_MAX_CAP_SIZE]-End--> |
| int32_t netCapsSize | 网络能力列表的实际size。<br><!--Device-int32_t netCapsSize--><!--Device-int32_t netCapsSize-End--> |
| [NetConn_NetBearerType](capi-net-connection-type-h.md#netconn_netbearertype) bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE] | 承载类型列表。<br><!--Device-NetConn_NetBearerType bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE]--><!--Device-NetConn_NetBearerType bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE]-End--> |
| int32_t bearerTypesSize | 承载类型列表的实际size。<br><!--Device-int32_t bearerTypesSize--><!--Device-int32_t bearerTypesSize-End--> |


