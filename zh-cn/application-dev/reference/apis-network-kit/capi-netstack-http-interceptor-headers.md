# OH_Http_Interceptor_Headers
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor_Headers {
    char *data;
    struct OH_Http_Interceptor_Headers *next;
} OH_Http_Interceptor_Headers;
```

## 概述

定义拦截器的请求/响应头信息。

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *data | 拦截器请求/响应头信息。 |
| struct OH_Http_Interceptor_Headers *next | 指向下一个头信息的指针。 |
