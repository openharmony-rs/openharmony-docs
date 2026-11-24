# Http_Response

```c
typedef struct Http_Response {...} Http_Response
```

## 概述

定义HTTP响应的结构体。

<!--Device-struct Http_Response {...}--><!--Device-struct Http_Response {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) body | HTTP请求响应的数据，参考[Http_Buffer](capi-netstack-http-buffer.md)。<br><!--Device-Http_Buffer body--><!--Device-Http_Buffer body-End--> |
| [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode) responseCode | HTTP请求响应码，参考[Http_ResponseCode](capi-net-http-type-h.md#http_responsecode)。<br><!--Device-Http_ResponseCode responseCode--><!--Device-Http_ResponseCode responseCode-End--> |
| [Http_Headers](capi-netstack-http-headers.md) *headers | HTTP响应的头，指向Http_Headers的指针，参考[Http_Headers](capi-netstack-http-headers.md)。<br><!--Device-Http_Headers *headers--><!--Device-Http_Headers *headers-End--> |
| char *cookies | HTTP响应Cookies。<br><!--Device-char *cookies--><!--Device-char *cookies-End--> |
| [Http_PerformanceTiming](capi-netstack-http-performancetiming.md) *performanceTiming | HTTP响应时间信息，指向Http_PerformanceTiming的指针，参考[Http_PerformanceTiming](capi-netstack-http-performancetiming.md)。<br><!--Device-Http_PerformanceTiming *performanceTiming--><!--Device-Http_PerformanceTiming *performanceTiming-End--> |


### 成员函数

| 名称 | 完整引用 | 描述 |
| -- | -- | -- |
| [void (\*destroyResponse)(struct Http_Response **response)](#destroyresponse) | destroyResponse | 销毁HTTP响应的回调函数 |

## 成员函数说明

### destroyResponse()

```c
void (*destroyResponse)(struct Http_Response **response)
```

**描述：**

销毁HTTP响应的回调函数

<!--Device-void (*destroyResponse)(struct Http_Response **response)--><!--Device-void (*destroyResponse)(struct Http_Response **response)-End-->

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| struct [Http_Response](capi-netstack-http-response.md) **response | 要销毁的HTTP响应，指向Http_Response的指针。 |


