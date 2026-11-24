# OH_Http_Interceptor_Request

```c
typedef struct OH_Http_Interceptor_Request {...} OH_Http_Interceptor_Request
```

## 概述

定义拦截器的HTTP请求数据包结构。

<!--Device-struct OH_Http_Interceptor_Request {...}--><!--Device-struct OH_Http_Interceptor_Request {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 24

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) url | 请求URL，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。<br>**起始版本：** 24<br><!--Device-Http_Buffer url--><!--Device-Http_Buffer url-End--> |
| [Http_Buffer](capi-netstack-http-buffer.md) method | 请求方法，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。<br>**起始版本：** 24<br><!--Device-Http_Buffer method--><!--Device-Http_Buffer method-End--> |
| [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) *headers | HTTP请求头信息，详情请参考[OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md)定义。<br>**起始版本：** 24<br><!--Device-OH_Http_Interceptor_Headers *headers--><!--Device-OH_Http_Interceptor_Headers *headers-End--> |
| [Http_Buffer](capi-netstack-http-buffer.md) body | 请求体内容，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。<br>**起始版本：** 24<br><!--Device-Http_Buffer body--><!--Device-Http_Buffer body-End--> |


