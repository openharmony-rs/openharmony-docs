# OH_Http_Interceptor_Response
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor_Response {
    Http_Buffer body;
    Http_ResponseCode responseCode;
    OH_Http_Interceptor_Headers *headers;
    Http_PerformanceTiming performanceTiming;
} OH_Http_Interceptor_Response;
```

## 概述

定义拦截器的HTTP响应数据包结构。

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| Http_Buffer body | 响应体内容，详情请参考[Http_Buffer](capi-netstack-http-buffer.md)定义。 |
| Http_ResponseCode responseCode | 响应状态码，详情请参考[Http_ResponseCode](capi-net-http-type-h.md#http_responsecode) 枚举定义。 |
| OH_Http_Interceptor_Headers *headers | HTTP响应头信息，详情请参考[OH_Http_Interceptor_Headers](capi-netstack-http-interceptor-headers.md)定义。 |
| Http_PerformanceTiming performanceTiming | 响应性能信息，详情请参考[Http_PerformanceTiming](capi-netstack-http-performancetiming.md)定义。 |
