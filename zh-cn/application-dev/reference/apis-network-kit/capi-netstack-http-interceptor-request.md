# OH_Http_Interceptor_Request
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor_Request {
    Http_Buffer url;
    Http_Buffer method;
    OH_Http_Interceptor_Headers *headers;
    Http_Buffer body;
} OH_Http_Interceptor_Request;
```

## 概述

定义拦截器的HTTP请求数据包结构。

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| Http_Buffer url | 请求URL，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。 |
| Http_Buffer method | 请求方法，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。 |
| OH_Http_Interceptor_Headers *headers | HTTP请求头信息，详情请参考[OH_Http_Interceptor_Headers](capi-netstack-http-interceptor-headers.md)定义。 |
| Http_Buffer body | 请求体内容，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。 |
