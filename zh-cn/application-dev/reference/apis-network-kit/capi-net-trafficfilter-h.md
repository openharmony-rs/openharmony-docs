# net_trafficfilter.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 概述

声明网络流量过滤与重定向功能的C接口。该头文件提供创建和销毁报文控制器、注册报文回调、添加和清除过滤规则，以及创建和销毁流量重定向器、添加和清除重定向规则的接口。<br> 适用于需要在系统层面对网络数据包进行拦截、过滤和重定向的应用场景。

**引用文件：** <network/netmanager_ext/net_trafficfilter.h>

**库：** libnet_trafficfilter.so

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)](#oh_trafficfilter_createredirector) | 创建流量重定向实例，用于将TCP流量重定向到代理服务器。资源管理：必须调用[OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector)释放资源。如果该函数失败，不会返回有效的重定向器。 |
| [int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_destroyredirector) | 销毁重定向实例并释放相关资源（包括规则），调用后句柄将失效。 |
| [int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)](#oh_trafficfilter_addredirectrule) | 添加TCP流量重定向规则，将匹配的流量重定向到指定的代理服务器。如需清除重定向规则，需要调用[OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule)。 |
| [int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_clearredirectrule) | 清除所有重定向规则。 |
| [int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)](#oh_trafficfilter_queryprocess) | 根据网络连接信息查询对应的进程信息。通过源IP、目的IP、源端口、目的端口和协议类型组成的五元组连接信息，查询发起该连接的进程信息。 |
| [int32_t OH_TrafficFilter_CreatePacketController(uint32_t group_id, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)](#oh_trafficfilter_createpacketcontroller) | 创建报文控制器实例，用于拦截和过滤网络报文。资源管理：必须调用[OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller)释放资源。如果该函数失败，不会返回有效的控制器。 |
| [int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_destroypacketcontroller) | 销毁报文控制器实例并释放相关资源（包括规则），调用后句柄将失效。 |
| [int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)](#oh_trafficfilter_registerpacketcallback) | 注册一个回调函数用于处理拦截到的报文，当报文匹配到过滤规则时，将触发该回调。 |
| [int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_unregisterpacketcallback) | 注销报文回调函数。 |
| [int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)](#oh_trafficfilter_addpacketrule) | 添加报文过滤规则，当报文匹配到该规则时，将触发报文回调。如需清除过滤规则，需要调用[OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule)。 |
| [int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_clearpacketrule) | 清除报文过滤规则。 |


## 函数说明

### OH_TrafficFilter_CreateRedirector()

```c
int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)
```

**描述**

创建流量重定向实例，用于将TCP流量重定向到代理服务器。资源管理：必须调用[OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector)释放资源。如果该函数失败，不会返回有效的重定向器。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t group_id | 重定向链标识符。这是应用内的逻辑分组ID。同一应用内的多个重定向器可以使用不同的group_id。不同应用的相同group_id会自动隔离。有效范围为[[OH_TRAFFICFILTER_MIN_GROUP_ID](capi-net-trafficfilter-type-h.md#宏定义), [OH_TRAFFICFILTER_MAX_GROUP_ID](capi-net-trafficfilter-type-h.md#宏定义)]，包含两个边界。如果group_id超出此范围，该函数返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。 |
| uint32_t priority | 优先级。决定不同group_id链之间的执行顺序，数值越小越先执行。注意：重定向器优先级高于报文过滤器优先级。有效范围为[[OH_TRAFFICFILTER_MIN_PRIORITY](capi-net-trafficfilter-type-h.md#宏定义), [OH_TRAFFICFILTER_MAX_PRIORITY](capi-net-trafficfilter-type-h.md#宏定义)]，包含两个边界。如果priority超出此范围，该函数返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。 |
| [OH_TrafficFilter_Redirector**](capi-trafficfilter-oh-trafficfilter-redirector.md) redirector | 出参，成功时为重定向句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - group_id已存在。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 参数错误。<br>     [OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - NFQueue初始化失败。 |

### OH_TrafficFilter_DestroyRedirector()

```c
int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)
```

**描述**

销毁重定向实例并释放相关资源（包括规则），调用后句柄将失效。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | OH_TrafficFilter_Redirector句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - redirector为NULL。<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 未找到指定的重定向器句柄。 |

### OH_TrafficFilter_AddRedirectRule()

```c
int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)
```

**描述**

添加TCP流量重定向规则，将匹配的流量重定向到指定的代理服务器。如需清除重定向规则，需要调用[OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule)。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | OH_TrafficFilter_Redirector句柄。 |
| [const OH_TrafficFilter_RedirectRule](capi-trafficfilter-oh-trafficfilter-redirectrule.md)* rule | 重定向规则。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - redirector或rule为NULL。<br>     [OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 添加的规则过多。 |

### OH_TrafficFilter_ClearRedirectRule()

```c
int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)
```

**描述**

清除所有重定向规则。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | OH_TrafficFilter_Redirector句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - redirector为NULL。 |

### OH_TrafficFilter_QueryProcess()

```c
int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)
```

**描述**

根据网络连接信息查询对应的进程信息。通过源IP、目的IP、源端口、目的端口和协议类型组成的五元组连接信息，查询发起该连接的进程信息。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)* connection_info | 输入的连接信息。 |
| [OH_TrafficFilter_ProcessInfo](capi-trafficfilter-oh-trafficfilter-processinfo.md)* process_info | 输出的进程信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 输入参数无效。<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 未找到进程。 |

### OH_TrafficFilter_CreatePacketController()

```c
int32_t OH_TrafficFilter_CreatePacketController(
    uint32_t group_id,
    uint32_t priority,
    const OH_TrafficFilter_Config* config,
    OH_TrafficFilter_PacketController** controller
)
```

**描述**

创建报文控制器实例。用于拦截和过滤网络报文。资源管理：该实例占用系统资源，必须调用[OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller)释放资源。如果该函数失败，不会返回有效的控制器。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t group_id | 过滤链标识符。同一应用内的多个控制器可以使用不同的group_id。不同应用的相同group_id会自动隔离。取值范围为[OH_TRAFFICFILTER_MIN_GROUP_ID, OH_TRAFFICFILTER_MAX_GROUP_ID]。 |
| uint32_t priority | 优先级（决定不同group_id链之间的执行顺序，数值越小执行优先级越高）。取值范围为[OH_TRAFFICFILTER_MIN_PRIORITY, OH_TRAFFICFILTER_MAX_PRIORITY]。 |
| [const OH_TrafficFilter_Config](capi-trafficfilter-oh-trafficfilter-config.md)* config | 配置参数（配置为NULL时表示使用默认配置）。 |
| [OH_TrafficFilter_PacketController**](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) controller | 出参，成功时为报文控制器句柄。失败时为NULL，句柄不可用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - group_id已存在。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - group_id或priority无效。<br>     [OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - NFQueue初始化失败。 |

### OH_TrafficFilter_DestroyPacketController()

```c
int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)
```

**描述**

销毁报文控制器实例。销毁控制器实例并释放相关资源（包括规则），调用后句柄将失效。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | OH_TrafficFilter_PacketController句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller为NULL。<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 未找到指定的控制器句柄。 |

### OH_TrafficFilter_RegisterPacketCallback()

```c
int32_t OH_TrafficFilter_RegisterPacketCallback(
    OH_TrafficFilter_PacketController* controller,
    OH_TrafficFilter_PacketCallback callback,
    void* userData
)
```

**描述**

注册报文回调函数。注册一个回调函数用于处理拦截到的报文，当报文匹配到过滤规则时，将触发该回调。如需释放回调，需调用OH_TrafficFilter_UnregisterPacketCallback。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | OH_TrafficFilter_PacketController句柄。 |
| [OH_TrafficFilter_PacketCallback](capi-trafficfilter-oh-trafficfilter-packetcallback.md) callback | 回调函数指针。不能为NULL。 |
| void* userData | 用户数据（将在回调中回传）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller或callback为NULL。 |

### OH_TrafficFilter_UnregisterPacketCallback()

```c
int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)
```

**描述**

注销报文回调函数。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | OH_TrafficFilter_PacketController句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller为NULL。 |

### OH_TrafficFilter_AddPacketRule()

```c
int32_t OH_TrafficFilter_AddPacketRule(
    OH_TrafficFilter_PacketController* controller,
    const OH_TrafficFilter_FilterRule* rule
)
```

**描述**

添加报文过滤规则。单个[OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md)结构内的条件为逻辑与关系。添加到同一[OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)的多个规则为逻辑或关系。如需清除过滤规则，需调用[OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule)。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | OH_TrafficFilter_PacketController句柄。 |
| [const OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md)* rule | 过滤规则。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller或rule为NULL。<br>     [OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 添加的规则超过2000条。 |

### OH_TrafficFilter_ClearPacketRule()

```c
int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)
```

**描述**

清除报文过滤规则（清除controller句柄上添加的所有报文过滤规则）。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**需要权限：** ohos.permission.kernel.TRAFFIC_FILTER

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | OH_TrafficFilter_PacketController句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 成功。<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - 缺少权限。<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller为NULL。 |
