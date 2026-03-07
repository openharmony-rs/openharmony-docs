# OH_Http_Interceptor
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor {
    int32_t groupId;
    OH_Interceptor_Stage stage;
    OH_Interceptor_Type type;
    OH_Http_InterceptorHandler handler;
    int32_t enabled;
} OH_Http_Interceptor;
```

## 概述

定义HTTP全局拦截器的配置信息。

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t groupId | 拦截器组ID。 |
| OH_Interceptor_Stage stage | 拦截器的执行阶段，详情请参考[OH_Interceptor_Stage](capi-net-http-interceptor-type-h.md#oh_interceptor_stage) 枚举定义。 |
| OH_Interceptor_Type type | 拦截器的类型，详情请参考[OH_Interceptor_Type](capi-net-http-interceptor-type-h.md#oh_interceptor_type) 枚举定义。 |
| OH_Http_InterceptorHandler handler | 拦截器处理函数，详情请参考[OH_Http_InterceptorHandler](capi-net-http-interceptor-type-h.md#oh_http_interceptorhandler) 函数指针定义。 |
| int32_t enabled | 拦截器的启用状态。 |
