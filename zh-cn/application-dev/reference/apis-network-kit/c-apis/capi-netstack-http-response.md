# Http_Response

```c
typedef struct Http_Response {...} Http_Response
```

## 概述

定义HTTP响应的结构体。

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) body | HTTP response data. For details, see [Http_Buffer](capi-netstack-http-buffer.md). |
| [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode) responseCode | HTTP response code. For details, see [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode). |
| [Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to the HTTP response header. For details, see [Http_Headers](capi-netstack-http-headers.md). |
| char *cookies | HTTP响应Cookies。 |
| [Http_PerformanceTiming](capi-netstack-http-performancetiming.md) *performanceTiming | Pointer to the HTTP response timing. For details, see [Http_PerformanceTiming](capi-netstack-http-performancetiming.md). |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [void (\*destroyResponse)(struct Http_Response **response)](#destroyresponse) | 销毁HTTP响应的回调函数 |

## 成员函数说明

### destroyResponse()

```c
void (*destroyResponse)(struct Http_Response **response)
```

**描述**

销毁HTTP响应的回调函数

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| struct [Http_Response](capi-netstack-http-response.md) **response | 要销毁的HTTP响应，指向Http_Response的指针。 |


