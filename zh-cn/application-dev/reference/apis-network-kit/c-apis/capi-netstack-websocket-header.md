# WebSocket_Header

```c
struct WebSocket_Header {...}
```

## 概述

WebSocket客户端增加header的链表节点。

<!--Device-struct WebSocket_Header {...}--><!--Device-struct WebSocket_Header {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_websocket_type.h](capi-net-websocket-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *fieldName | header的字段名。<br><!--Device-const char *fieldName--><!--Device-const char *fieldName-End--> |
| const char *fieldValue | header的字段内容。<br><!--Device-const char *fieldValue--><!--Device-const char *fieldValue-End--> |
| [struct WebSocket_Header](capi-netstack-websocket-header.md) *next | header链表的next指针。<br><!--Device-struct WebSocket_Header *next--><!--Device-struct WebSocket_Header *next-End--> |


