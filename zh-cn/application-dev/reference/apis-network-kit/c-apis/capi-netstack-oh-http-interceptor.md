# OH_Http_Interceptor

```c
typedef struct OH_Http_Interceptor {...} OH_Http_Interceptor
```

## 概述

定义HTTP全局拦截器的配置信息。

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t groupId | 拦截器组ID。<br>**起始版本：** 24 |
| [OH_Interceptor_Stage](capi-http-interceptor-type-h.md#oh_interceptor_stage) stage | 拦截器的执行阶段，详情请参考[OH_Interceptor_Stage](capi-http-interceptor-type-h.md#oh_interceptor_stage) 枚举定义。<br>**起始版本：** 24 |
| [OH_Interceptor_Type](capi-http-interceptor-type-h.md#oh_interceptor_type) type | 拦截器的类型，详情请参考[OH_Interceptor_Type](capi-http-interceptor-type-h.md#oh_interceptor_type) 枚举定义。<br>**起始版本：** 24 |
| [OH_Http_InterceptorHandler](capi-http-interceptor-type-h.md#oh_http_interceptorhandler) handler | 拦截器处理函数，详情请参考[OH_Http_InterceptorHandler](capi-http-interceptor-type-h.md#oh_http_interceptorhandler) 函数指针定义。<br>**起始版本：** 24 |
| int32_t enabled | 拦截器的启用状态。0代表未启用，非0代表启用。<br>**起始版本：** 24 |


