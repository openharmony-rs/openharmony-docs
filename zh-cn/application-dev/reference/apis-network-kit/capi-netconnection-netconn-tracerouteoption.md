# NetConn_TraceRouteOption

## 概述

定义网络跟踪路由选项。

**起始版本：** 20

**相关模块：** [NetConnection](capi-netconnection.md)

**所在头文件：** [net_connection_type.h](capi-net-connection-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t maxJumpNumber | 探测结果最大跳数，需要和TraceRouteInfo设置一致，最大可设置30跳，默认为30跳。 |
| NetConn_PacketsType packetsType | 探测包协议类型，默认为NETCONN_PACKETS_ICMP。 |