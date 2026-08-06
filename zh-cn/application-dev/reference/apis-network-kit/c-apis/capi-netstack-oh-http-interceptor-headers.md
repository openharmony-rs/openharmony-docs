# OH_Http_Interceptor_Headers

```c
typedef struct OH_Http_Interceptor_Headers {...} OH_Http_Interceptor_Headers
```

## 概述

定义拦截器的请求/响应头信息。

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *data | 拦截器请求/响应头信息。<br>**起始版本：** 24 |
| struct [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) *next | 指向下一个头信息的指针。<br>**起始版本：** 24 |


