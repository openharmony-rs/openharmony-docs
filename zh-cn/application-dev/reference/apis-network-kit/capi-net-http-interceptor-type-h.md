# http_interceptor_type.h
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 概述

为HTTP全局拦截器模块提供C接口的数据结构定义，包含拦截器的请求/响应头信息、HTTP请求/响应数据包结构、拦截器配置信息以及相关的枚举类型和函数指针。

**引用文件：** <network/netstack/http_interceptor_type.h>

**库：** libhttp_interceptor.so

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Http_Interceptor_Headers](capi-netstack-http-interceptor-headers.md) | OH_Http_Interceptor_Headers | 定义拦截器的请求/响应头信息。 |
| [OH_Http_Interceptor_Request](capi-netstack-http-interceptor-request.md) | OH_Http_Interceptor_Request | 定义拦截器的HTTP请求数据包结构。 |
| [OH_Http_Interceptor_Response](capi-netstack-http-interceptor-response.md) | OH_Http_Interceptor_Response | 定义拦截器的HTTP响应数据包结构。 |
| [OH_Http_Interceptor](capi-netstack-http-interceptor.md) | OH_Http_Interceptor | 定义HTTP全局拦截器的配置信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Interceptor_Stage](#oh_interceptor_stage) | OH_Interceptor_Stage | 定义拦截器的执行阶段。 |
| [OH_Interceptor_Type](#oh_interceptor_type) | OH_Interceptor_Type | 定义拦截器的类型。 |
| [OH_Interceptor_Result](#oh_interceptor_result) | OH_Interceptor_Result | 定义拦截器的处理结果。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef OH_Interceptor_Result (*OH_Http_InterceptorHandler)(OH_Http_Interceptor_Request *request, OH_Http_Interceptor_Response *response, int32_t *isModified)](#oh_http_interceptorhandler) | OH_Http_InterceptorHandler | 指向HTTP拦截器处理函数的指针。 |

## 枚举类型说明

### OH_Interceptor_Stage

```c
enum OH_Interceptor_Stage
```

**描述**

定义拦截器的执行阶段。

**起始版本：** 24

**参数：**
| 枚举项 | 描述 |
| -- | -- |
| OH_STAGE_REQUEST | 拦截器处理请求。 |
| OH_STAGE_RESPONSE | 拦截器处理响应。 |

### OH_Interceptor_Type

```c
enum OH_Interceptor_Type
```

**描述**

定义拦截器的类型。

**起始版本：** 24

**参数：**
| 枚举项 | 描述 |
| -- | -- |
| OH_TYPE_READ_ONLY | 只读拦截器。|

### OH_Interceptor_Result

```c
enum OH_Interceptor_Result
```

**描述**

定义拦截器的处理结果。

**起始版本：** 24

**参数：**
| 枚举项 | 描述 |
| -- | -- |
| OH_CONTINUE | 继续处理。 |
| OH_ABORT | 拦截处理。 |

## 函数说明

### OH_Http_InterceptorHandler()

```c
typedef OH_Interceptor_Result (*OH_Http_InterceptorHandler)(
    OH_Http_Interceptor_Request *request,
    OH_Http_Interceptor_Response *response,
    int32_t *isModified)
```

**描述**

定义HTTP拦截器处理函数。

**起始版本：** 24

**参数：**
| 参数项 | 描述 |
| -- | -- |
| [OH_Http_Interceptor_Request](capi-netstack-http-interceptor-request.md) *request| HTTP请求数据包指针（仅在请求阶段有效）。 |
| [OH_Http_Interceptor_Response](capi-netstack-http-interceptor-response.md) *response| HTTP响应数据包指针（仅在响应阶段有效）。 |
| int32_t *isModified | 标识拦截器是否修改了数据包。对OH_TYPE_READ_ONLY类型拦截器无效，可配置为nullptr。<br>- 0表示未对数据执行修改操作。<br>- 非0表示已对数据执行修改操作。 |

**返回：**

| 类型                                            | 说明                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_Interceptor_Result](#oh_interceptor_result) | 拦截器处理结果。<br>- OH_CONTINUE：继续处理 <br>- OH_ABORT：拦截处理 |