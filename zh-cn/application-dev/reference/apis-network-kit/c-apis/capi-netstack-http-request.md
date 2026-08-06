# Http_Request

```c
typedef struct Http_Request {...} Http_Request
```

## 概述

HTTP请求结构体。

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t requestId | HTTP请求的ID。 |
| char *url | HTTP请求的URL。 |
| [Http_RequestOptions](capi-netstack-http-requestoptions.md) *options | Pointer to the HTTP request configuration. For details, see [Http_RequestOptions](capi-netstack-http-requestoptions.md). |


