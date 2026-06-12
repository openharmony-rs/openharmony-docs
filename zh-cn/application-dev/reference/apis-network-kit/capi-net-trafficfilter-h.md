# net-trafficfilter.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 概述

定义流量过滤模块的接口。通过流量重定向能力，开发者可以创建透明 TCP 流量重定向实例，将匹配规则的流量重定向到指定代理服务器；同时支持根据连接五元组查询对应进程信息。

- **重定向能力限制**：当前重定向规则仅支持 TCP 流量。重定向目标需要同时配置合法的代理 IP 地址和代理端口。
- **IPv4/IPv6 支持**：源地址、目的地址和代理地址均支持 IPv4 和 IPv6。
- **资源管理要求**：通过 `OH_TrafficFilter_CreateRedirector` 创建的重定向实例会占用系统资源，开发者必须调用 `OH_TrafficFilter_DestroyRedirector` 释放资源。
- **规则管理要求**：通过 `OH_TrafficFilter_AddRedirectRule` 添加的规则会持续生效，直到调用 `OH_TrafficFilter_ClearRedirectRule` 清除规则，或销毁对应 redirector。
- **结构体 size 要求**：包含 `size` 字段的结构体必须由调用方填写实际分配的结构体大小。库侧根据 `size` 判断可访问字段范围。
- **权限要求**：调用接口需要具备 `ohos.permission.kernel.TRAFFIC_FILTER` 权限。

**引用文件：** `<network/netmanager_ext/net_trafficfilter.h>`

**库：** `libnet_trafficfilter.so`

**系统能力：** `SystemCapability.Communication.NetManager.NetFirewall`

**起始版本：** 26.0.0

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector **redirector)](#oh_trafficfilter_createredirector) | 创建一个流量重定向实例。 |
| [int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector *redirector)](#oh_trafficfilter_destroyredirector) | 销毁流量重定向实例并释放相关资源。 |
| [int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector *redirector, const OH_TrafficFilter_RedirectRule *rule)](#oh_trafficfilter_addredirectrule) | 添加一条 TCP 流量重定向规则。 |
| [int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector *redirector)](#oh_trafficfilter_clearredirectrule) | 清除指定重定向实例下的所有重定向规则。 |
| [int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo *connection_info, OH_TrafficFilter_ProcessInfo *process_info)](#oh_trafficfilter_queryprocess) | 根据连接五元组信息查询对应进程信息。 |

## 函数说明

### OH_TrafficFilter_CreateRedirector()

```c
int32_t OH_TrafficFilter_CreateRedirector(
    uint32_t group_id,
    uint32_t priority,
    OH_TrafficFilter_Redirector** redirector
)
```

**描述**

创建一个流量重定向实例，用于将匹配规则的透明 TCP 流量重定向到指定代理服务器。

- 创建成功后会返回一个 `OH_TrafficFilter_Redirector` 句柄。
- 该实例会占用系统资源，必须调用 [OH_TrafficFilter_DestroyRedirector](#oh_trafficfilter_destroyredirector) 释放。
- 如果创建失败，不会返回有效的 redirector。
- `group_id` 是应用内的逻辑分组 ID。
- 同一应用内不同 redirector 应使用不同的 `group_id`。
- 不同应用使用相同 `group_id` 时会自动隔离。
- `priority` 用于决定不同 `group_id` 对应重定向链之间的执行顺序，数值越小优先级越高。
- 重定向器优先级高于包过滤优先级。

**系统能力：** `SystemCapability.Communication.NetManager.NetFirewall`

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| `uint32_t group_id` | 重定向链标识。应用内逻辑分组 ID。同一应用内不能重复使用相同 `group_id`。取值范围为 [`OH_TRAFFICFILTER_MIN_GROUP_ID`, `OH_TRAFFICFILTER_MAX_GROUP_ID`]，超出范围返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。 |
| `uint32_t priority` | 重定向器优先级。数值越小优先级越高。取值范围为 [`OH_TRAFFICFILTER_MIN_PRIORITY`, `OH_TRAFFICFILTER_MAX_PRIORITY`]，超出范围返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。 |
| `OH_TrafficFilter_Redirector **redirector` | 输出参数。创建成功时返回重定向实例句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| `int32_t` | 返回 `OH_TRAFFICFILTER_OK` 表示成功；返回 `OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED` 表示权限被拒绝；返回 `OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE` 表示 `group_id` 已存在；返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM` 表示参数非法；返回 `OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR` 表示 NFQueue 初始化失败。 |

**权限：** `ohos.permission.kernel.TRAFFIC_FILTER`

**资源释放：** 调用 [OH_TrafficFilter_DestroyRedirector](#oh_trafficfilter_destroyredirector) 释放 `redirector`。

**起始版本：** 26.0.0

### OH_TrafficFilter_DestroyRedirector()

```c
int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)
```

**描述**

销毁指定流量重定向实例，并释放相关资源。

- 销毁时会清理该 redirector 下的重定向规则。
- 销毁后，该句柄失效，不能继续使用。

**系统能力：** `SystemCapability.Communication.NetManager.NetFirewall`

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| `OH_TrafficFilter_Redirector *redirector` | 待销毁的流量重定向实例句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| `int32_t` | 返回 `OH_TRAFFICFILTER_OK` 表示成功；返回 `OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED` 表示权限被拒绝；返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM` 表示 `redirector` 为空；返回 `OH_TRAFFICFILTER_ERROR_NOT_FOUND` 表示指定的 redirector 句柄未找到。 |

**权限：** `ohos.permission.kernel.TRAFFIC_FILTER`

**起始版本：** 26.0.0

### OH_TrafficFilter_AddRedirectRule()

```c
int32_t OH_TrafficFilter_AddRedirectRule(
    OH_TrafficFilter_Redirector* redirector,
    const OH_TrafficFilter_RedirectRule* rule
)
```

**描述**

添加一条 TCP 流量重定向规则，将匹配条件的流量重定向到指定代理服务器。

- 当前仅支持 TCP 流量重定向。
- `redirector` 不能为空。
- `rule` 不能为空。
- `rule` 中的 `size` 字段必须由调用方填写为实际分配的结构体大小。
- `rule` 的匹配条件可包含源 IP、源端口、目的 IP、目的端口、入接口、出接口、UID 范围等。
- 代理地址 `proxy_ip` 支持 IPv4 和 IPv6。
- 代理端口 `proxy_port` 必须为有效端口，不能为 0。
- IPv4 规则必须使用 IPv4 代理地址，IPv6 规则必须使用 IPv6 代理地址。
- 清除重定向规则需要调用 [OH_TrafficFilter_ClearRedirectRule](#oh_trafficfilter_clearredirectrule)。

**系统能力：** `SystemCapability.Communication.NetManager.NetFirewall`

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| `OH_TrafficFilter_Redirector *redirector` | 重定向实例句柄。不能为空。 |
| `const OH_TrafficFilter_RedirectRule *rule` | 重定向规则。不能为空。调用方必须正确设置 `rule->size`。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| `int32_t` | 返回 `OH_TRAFFICFILTER_OK` 表示成功；返回 `OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED` 表示权限被拒绝；返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM` 表示参数非法，例如 `redirector` 或 `rule` 为空、`rule->size` 非法、规则字段非法；返回 `OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES` 表示添加规则数量超过限制。 |

**权限：** `ohos.permission.kernel.TRAFFIC_FILTER`

**起始版本：** 26.0.0

### OH_TrafficFilter_ClearRedirectRule()

```c
int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)
```

**描述**

清除指定重定向实例下的所有流量重定向规则。

- `redirector` 不能为空。
- 清除后，该 redirector 仍然有效，可以继续添加新的重定向规则。
- 该接口只清除规则，不销毁 redirector。
- 若需要释放 redirector 资源，应调用 [OH_TrafficFilter_DestroyRedirector](#oh_trafficfilter_destroyredirector)。

**系统能力：** `SystemCapability.Communication.NetManager.NetFirewall`

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| `OH_TrafficFilter_Redirector *redirector` | 重定向实例句柄。不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| `int32_t` | 返回 `OH_TRAFFICFILTER_OK` 表示成功；返回 `OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED` 表示权限被拒绝；返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM` 表示 `redirector` 为空或无效。 |

**权限：** `ohos.permission.kernel.TRAFFIC_FILTER`

**起始版本：** 26.0.0

### OH_TrafficFilter_QueryProcess()

```c
int32_t OH_TrafficFilter_QueryProcess(
    const OH_TrafficFilter_ConnectionInfo* connection_info,
    OH_TrafficFilter_ProcessInfo* process_info
)
```

**描述**

根据连接五元组信息查询对应进程信息。

- 五元组信息包括源 IP、源端口、目的 IP、目的端口和协议。
- 支持 IPv4 和 IPv6。
- 支持 TCP 和 UDP 协议。
- `connection_info` 不能为空。
- `connection_info->size` 必须由调用方填写为实际分配的结构体大小。
- `process_info` 不能为空。
- `process_info->size` 必须由调用方填写为实际分配的结构体大小。
- 查询成功时，库侧只会回填 `process_info->size` 覆盖范围内的字段。
- `src_port` 为 0 表示任意源端口。
- `dst_port` 为 0 表示任意目的端口。
- 当端口为 0 且匹配到多个连接时，返回第一个匹配到的进程信息。

**系统能力：** `SystemCapability.Communication.NetManager.NetFirewall`

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| `const OH_TrafficFilter_ConnectionInfo *connection_info` | 输入连接信息。包含源 IP、源端口、目的 IP、目的端口和协议。调用方必须正确设置 `connection_info->size`。 |
| `OH_TrafficFilter_ProcessInfo *process_info` | 输出进程信息。调用方必须正确设置 `process_info->size`。查询成功时仅回填 `size` 覆盖范围内的字段。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| `int32_t` | 返回 `OH_TRAFFICFILTER_OK` 表示成功；返回 `OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED` 表示权限被拒绝；返回 `OH_TRAFFICFILTER_ERROR_INVALID_PARAM` 表示输入参数非法；返回 `OH_TRAFFICFILTER_ERROR_NOT_FOUND` 表示未找到对应进程。 |

**权限：** `ohos.permission.kernel.TRAFFIC_FILTER`

**起始版本：** 26.0.0
