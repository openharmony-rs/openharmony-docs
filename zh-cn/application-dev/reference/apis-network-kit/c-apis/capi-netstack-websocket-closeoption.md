# WebSocket_CloseOption

```c
struct WebSocket_CloseOption {...}
```

## 概述

WebSocket客户端主动关闭的参数。

<!--Device-struct WebSocket_CloseOption {...}--><!--Device-struct WebSocket_CloseOption {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_websocket_type.h](capi-net-websocket-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t code | 错误值。<br><!--Device-uint32_t code--><!--Device-uint32_t code-End--> |
| const char *reason | 错误原因。<br><!--Device-const char *reason--><!--Device-const char *reason-End--> |


