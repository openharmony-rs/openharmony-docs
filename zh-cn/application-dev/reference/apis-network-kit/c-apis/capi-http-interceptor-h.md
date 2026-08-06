# http_interceptor.h

## 概述

定义HTTP全局拦截器模块的接口，分为只读拦截器与可修改拦截器两类。通过全局只读拦截器，开发者可以监控应用内部通过所支持的系统网络组件发起的所有HTTP请求，实现日志记录功能，也可以在全局可修改拦截器中添加自定义逻辑，修改应用内部通过所支持的系统网络组件发起的HTTP请求的请求头、响应头、响应体。

**库：** libhttp_interceptor.so

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 24

**相关模块：** [netstack](capi-netstack.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_Http_AddReadOnlyInterceptor(struct OH_Http_Interceptor *interceptor)](#oh_http_addreadonlyinterceptor) | 添加一个HTTP全局只读拦截器。 |
| [int32_t OH_Http_AddWritableInterceptor(struct OH_Http_Interceptor *interceptor)](#oh_http_addwritableinterceptor) | 添加一个HTTP全局可修改拦截器。 |
| [int32_t OH_Http_RemoveInterceptor(struct OH_Http_Interceptor *interceptor)](#oh_http_removeinterceptor) | 删除指定的HTTP全局拦截器。 |
| [int32_t OH_Http_RemoveAllInterceptors(int32_t groupId)](#oh_http_removeallinterceptors) | 删除指定组ID的所有HTTP拦截器。 |
| [int32_t OH_Http_StartAllInterceptors(int32_t groupId)](#oh_http_startallinterceptors) | 启用指定组ID的所有HTTP拦截器。 |
| [int32_t OH_Http_StopAllInterceptors(int32_t groupId)](#oh_http_stopallinterceptors) | 停用指定组ID的所有HTTP拦截器。 |

## 函数说明

### OH_Http_AddReadOnlyInterceptor()

```c
int32_t OH_Http_AddReadOnlyInterceptor(struct OH_Http_Interceptor *interceptor)
```

**描述**

添加一个HTTP全局只读拦截器。

>**说明：** 
>The interceptor remains active until it is explicitly removed by the developer.
 *     you must call [OH_Http_RemoveInterceptor](capi-http-interceptor-h.md#oh_http_removeinterceptor) to release a specific interceptor
 *     or [OH_Http_RemoveAllInterceptors](capi-http-interceptor-h.md#oh_http_removeallinterceptors) to release a group of interceptors.

**需要权限：** ohos.permission.INTERNET

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_Http_Interceptor](capi-netstack-oh-http-interceptor.md) *interceptor | 待添加的拦截器，指向OH_Http_Interceptor结构体的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；返回值为201表示权限被拒绝；返回值为401表示参数错误。 |

### OH_Http_AddWritableInterceptor()

```c
int32_t OH_Http_AddWritableInterceptor(struct OH_Http_Interceptor *interceptor)
```

**描述**

添加一个HTTP全局可修改拦截器。

>**说明：** 
>The interceptor remains active until it is explicitly removed by the developer.
 *     you must call [OH_Http_RemoveInterceptor](capi-http-interceptor-h.md#oh_http_removeinterceptor) to release a specific interceptor
 *     or [OH_Http_RemoveAllInterceptors](capi-http-interceptor-h.md#oh_http_removeallinterceptors) to release a group of interceptors.

**需要权限：** ohos.permission.INTERNET

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_Http_Interceptor](capi-netstack-oh-http-interceptor.md) *interceptor | 待添加的拦截器，指向OH_Http_Interceptor结构体的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；返回值为201表示权限被拒绝；返回值为401表示参数错误。 |

### OH_Http_RemoveInterceptor()

```c
int32_t OH_Http_RemoveInterceptor(struct OH_Http_Interceptor *interceptor)
```

**描述**

删除指定的HTTP全局拦截器。

**需要权限：** ohos.permission.INTERNET

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_Http_Interceptor](capi-netstack-oh-http-interceptor.md) *interceptor | 待删除的拦截器，指向OH_Http_Interceptor结构体的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；返回值为201表示权限被拒绝；返回值为401表示参数错误。 |

### OH_Http_RemoveAllInterceptors()

```c
int32_t OH_Http_RemoveAllInterceptors(int32_t groupId)
```

**描述**

删除指定组ID的所有HTTP拦截器。

>**说明：** 
>The groupId is allocated and managed by the application itself when creating
 *     interceptors. If multiple modules within the application need to use interceptors,
 *     the application must properly allocate and manage groupId to avoid conflicts.
 *     Conflicts in groupId between internal modules may lead to accidental deletion
 *     of interceptors when calling this function.

**需要权限：** ohos.permission.INTERNET

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t groupId | 拦截器组ID。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；返回值为201表示权限被拒绝；返回值为401表示参数错误。 |

### OH_Http_StartAllInterceptors()

```c
int32_t OH_Http_StartAllInterceptors(int32_t groupId)
```

**描述**

启用指定组ID的所有HTTP拦截器。

**需要权限：** ohos.permission.INTERNET

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t groupId | http global interceptor group id |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_HTTP_RESULT_OK](capi-net-http-type-h.md#http_errcode) 0 -if the operation is successful.<br>     [OH_HTTP_PERMISSION_DENIED](capi-net-http-type-h.md#http_errcode) 201 -if permission is denied. |

### OH_Http_StopAllInterceptors()

```c
int32_t OH_Http_StopAllInterceptors(int32_t groupId)
```

**描述**

停用指定组ID的所有HTTP拦截器。

**需要权限：** ohos.permission.INTERNET

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t groupId | http global interceptor group id |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_HTTP_RESULT_OK](capi-net-http-type-h.md#http_errcode) 0 -if the operation is successful.<br>     [OH_HTTP_PERMISSION_DENIED](capi-net-http-type-h.md#http_errcode) 201 -if permission is denied. |


