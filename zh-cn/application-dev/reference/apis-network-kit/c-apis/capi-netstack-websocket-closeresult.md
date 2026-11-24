# WebSocket_CloseResult

```c
struct WebSocket_CloseResult {...}
```

## 概述

WebSocket客户端接收到服务端关闭的参数。

<!--Device-struct WebSocket_CloseResult {...}--><!--Device-struct WebSocket_CloseResult {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_websocket_type.h](capi-net-websocket-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t code | 错误码。<br><!--Device-uint32_t code--><!--Device-uint32_t code-End--> |
| const char *reason | 错误原因。<br><!--Device-const char *reason--><!--Device-const char *reason-End--> |


