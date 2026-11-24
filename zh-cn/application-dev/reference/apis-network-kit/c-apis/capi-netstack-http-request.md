# Http_Request

```c
typedef struct Http_Request {...} Http_Request
```

## 概述

HTTP请求结构体。

<!--Device-struct Http_Request {...}--><!--Device-struct Http_Request {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t requestId | HTTP请求的ID。<br><!--Device-uint32_t requestId--><!--Device-uint32_t requestId-End--> |
| char *url | HTTP请求的URL。<br><!--Device-char *url--><!--Device-char *url-End--> |
| [Http_RequestOptions](capi-netstack-http-requestoptions.md) *options | HTTP请求配置，指向Http_RequestOptions的指针，参考[Http_RequestOptions](capi-netstack-http-requestoptions.md)。<br><!--Device-Http_RequestOptions *options--><!--Device-Http_RequestOptions *options-End--> |


