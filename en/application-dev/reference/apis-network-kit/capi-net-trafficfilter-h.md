# net_trafficfilter.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=0eaa83d364c648e440aae918345f7154b12bb85b translatedAt=2026-08-12T11:08:05.919Z pushedAt=2026-08-13T03:49:32.880Z -->

## Overview

Declares the C APIs for network traffic filtering and redirection. This header file provides APIs for creating and destroying a packet controller, registering packet callbacks, adding and deleting filtering rules, creating and destroying a traffic redirector, and adding and deleting redirection rules.<br> It is applicable to scenarios where network packets need to be intercepted, filtered, and redirected at the system level.

**File to include:** <network/netmanager_ext/net_trafficfilter.h>

**Library:** libnet_trafficfilter.so

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module:** [TrafficFilter](capi-trafficfilter.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)](#oh_trafficfilter_createredirector) | Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) must be called to release resources. If this function fails, no valid redirector is returned. |
| [int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_destroyredirector) | Destroys the redirection instance and releases related resources (including rules). The handle becomes invalid after the function is called. |
| [int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)](#oh_trafficfilter_addredirectrule) | Adds a TCP traffic redirection rule to redirect matching traffic to the specified proxy server. To delete a redirection rule, call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule). |
| [int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_clearredirectrule) | Clears all redirection rules. |
| [int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)](#oh_trafficfilter_queryprocess) | Queries the process information based on network connection. This function queries the process that starts the connection using the five-tuple connection information, including the source IP address, destination IP address, source port, destination port, and protocol type. |

## Function Description

### OH_TrafficFilter_CreateRedirector()

```c
int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)
```

**Description**

Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) must be called to release resources. If this function fails, no valid redirector is returned.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| uint32_t group_id | Redirection link ID, which is a logical group ID within an app. Different **group_id** values can be used for multiple redirectors within the same app. Redirectors with the same **group_id** in different apps are automatically isolated. The value range is [[OH_TRAFFICFILTER_MIN_GROUP_ID](capi-net-trafficfilter-type-h.md#macros), [OH_TRAFFICFILTER_MAX_GROUP_ID](capi-net-trafficfilter-type-h.md#macros)]. If the value is out of this range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| uint32_t priority | Priority, which determines the execution order among links with different **group_id** values. A smaller value indicates a higher priority. Note: The redirector priority is higher than the packet filter priority. The value range is [[OH_TRAFFICFILTER_MIN_PRIORITY](capi-net-trafficfilter-type-h.md#macros), [OH_TRAFFICFILTER_MAX_PRIORITY](capi-net-trafficfilter-type-h.md#macros)]. If the value is out of range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| redirector | Output parameter, which is the redirection handle when the operation is successful. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.<br>     [OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **group_id** exists.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Parameter error. |

### OH_TrafficFilter_DestroyRedirector()

```c
int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Destroys the redirection instance and releases related resources (including rules). The handle becomes invalid after the function is called.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Handle of **OH_TrafficFilter_Redirector**. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **redirector** value is **NULL**.<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The specified redirector handle is not found. |

### OH_TrafficFilter_AddRedirectRule()

```c
int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)
```

**Description**

Adds a TCP traffic redirection rule to redirect matching traffic to the specified proxy server. To delete a redirection rule, call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule).

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Handle of **OH_TrafficFilter_Redirector**. |
| rule | Redirection rule, which cannot be **NULL**. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **redirector** or **rule** value is **NULL**.<br>     [OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Too many rules added. |

### OH_TrafficFilter_ClearRedirectRule()

```c
int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Clears all redirection rules.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Handle of **OH_TrafficFilter_Redirector**. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **redirector** value is NULL. |

### OH_TrafficFilter_QueryProcess()

```c
int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)
```

**Description**

Queries the process information based on network connection. This function queries the process that starts the connection using the five-tuple connection information, including the source IP address, destination IP address, source port number, destination port number, and protocol type.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)* connection_info | Input connection information. |
| process_info | Output process information. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Invalid input parameter.<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Process not found. |
<!--no_check-->