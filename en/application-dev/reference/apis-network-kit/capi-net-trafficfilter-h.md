# net_trafficfilter.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a95ecad3c50b68f98285a59d286e46aa2c99b901 translatedAt=2026-11-04T06:28:40.259Z pushedAt=2026-11-04T08:04:44.843Z nl=1 -->

## Overview

Declares the C APIs for network traffic filtering and redirection. This header file provides APIs for creating and destroying a packet controller, registering packet callbacks, adding and clearing filter rules, as well as creating and destroying a traffic redirector and adding and clearing redirection rules.<br> It applies to scenarios where network packets need to be intercepted, filtered, and redirected at the system level.

**File to include:** <network/netmanager_ext/net_trafficfilter.h>

**Library:** libnet_trafficfilter.so

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**Since:** 26.0.0

**Related module:** [TrafficFilter](capi-trafficfilter.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)](#oh_trafficfilter_createredirector) | Creates a traffic redirection instance to redirect TCP traffic to a proxy server. Resource management: You must call [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) to release resources. If this function fails, no valid redirector is returned. |
| [int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_destroyredirector) | Destroys the redirection instance and releases related resources (including rules). After the call, the handle becomes invalid. |
| [int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)](#oh_trafficfilter_addredirectrule) | Adds a TCP traffic redirection rule to redirect matching traffic to the specified proxy server. To clear the redirection rules, call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule). |
| [int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_clearredirectrule) | Clears all redirection rules. |
| [int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)](#oh_trafficfilter_queryprocess) | Queries the corresponding process information based on the network connection information. Queries the process that initiates a connection based on the five-tuple connection information consisting of the source IP address, destination IP address, source port, destination port, and protocol type. |
| [int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)](#oh_trafficfilter_createpacketcontroller) | Creates a packet controller instance for intercepting and filtering network packets. Resource management: Must call [OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to release resources. If the function fails, it will not return a valid controller. |
| [int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_destroypacketcontroller) | Destroys a packet controller instance and releases related resources (including rules). After calling, the handle will become invalid. |
| [int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)](#oh_trafficfilter_registerpacketcallback) | Registers a callback function for processing intercepted packets. When a packet matches the filtering rules, the callback is triggered. |
| [int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_unregisterpacketcallback) | Unregisters the packet callback function. |
| [int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)](#oh_trafficfilter_addpacketrule) | Adds a packet filtering rule. When a packet matches the rule, the packet callback is triggered. To clear the filtering rules, need to call [OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule). |
| [int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_clearpacketrule) | Clears the packet filtering rules. |


## Function Description

### OH_TrafficFilter_CreateRedirector()

```c
int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)
```

**Description**

Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. Resource management: You must call [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) to release the resources. If this function fails, no valid redirector is returned.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| uint32_t group_id | Redirection chain identifier. This is a logical group ID within an app. Multiple redirectors in the same app can use different **group_id** values. The same **group_id** in different apps is automatically isolated. The valid range is [[OH_TRAFFICFILTER_MIN_GROUP_ID](capi-net-trafficfilter-type-h.md#macros), [OH_TRAFFICFILTER_MAX_GROUP_ID](capi-net-trafficfilter-type-h.md#macros)], inclusive of both boundaries. If **group_id** is out of this range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| uint32_t priority | Priority. Determines the execution order among chains with different **group_id** values. A smaller value indicates earlier execution. Note: The redirector priority is higher than the packet filter priority. The valid range is [[OH_TRAFFICFILTER_MIN_PRIORITY](capi-net-trafficfilter-type-h.md#macros), [OH_TRAFFICFILTER_MAX_PRIORITY](capi-net-trafficfilter-type-h.md#macros)], inclusive of both boundaries. If priority is out of this range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| [OH_TrafficFilter_Redirector**](capi-trafficfilter-oh-trafficfilter-redirector.md) redirector | Output parameter, which is the redirector handle on success. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Permission denied.<br>     [OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - **group_id** already exists.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Invalid parameter. |

### OH_TrafficFilter_DestroyRedirector()

```c
int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Destroys a redirection instance and releases related resources (including rules). After this API is called, the handle becomes invalid.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Handle to the **OH_TrafficFilter_Redirector**. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Permission denied.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - **redirector** is NULL.<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - The specified redirector handle is not found. |

### OH_TrafficFilter_AddRedirectRule()

```c
int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)
```

**Description**

Adds a TCP traffic redirection rule to redirect matching traffic to the specified proxy server. To clear the redirection rule, call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule).

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Handle to the **OH_TrafficFilter_Redirector**. |
| [const OH_TrafficFilter_RedirectRule](capi-trafficfilter-oh-trafficfilter-redirectrule.md)* rule | Redirection rules. Cannot be NULL. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Permission denied.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - **redirector** or **rule** is NULL.<br>     [OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Too many rules are added. |

### OH_TrafficFilter_ClearRedirectRule()

```c
int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Clears all redirection rules.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Handle to **OH_TrafficFilter_Redirector**. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Permission denied.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - **redirector** is NULL. |

### OH_TrafficFilter_QueryProcess()

```c
int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)
```

**Description**

Queries the process information corresponding to the network connection information. Queries the process that initiates a connection based on the five-tuple connection information consisting of the source IP address, destination IP address, source port, destination port, and protocol type.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [const OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)* connection_info | Input connection information. |
| [OH_TrafficFilter_ProcessInfo](capi-trafficfilter-oh-trafficfilter-processinfo.md)* process_info | Pointer to the output process information. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Permission denied.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Invalid input parameter.<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Process not found. |

### OH_TrafficFilter_CreatePacketController()

```c
int32_t OH_TrafficFilter_CreatePacketController(
    uint32_t groupId,
    uint32_t priority,
    const OH_TrafficFilter_Config* config,
    OH_TrafficFilter_PacketController** controller
)
```

**Description**

Creates a packet controller instance. It is used to intercept and filter network packets. Resource management: This instance occupies system resources. You must call [OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to release resources. If the function fails, it will not return a valid controller.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| uint32_t groupId | Filter chain identifier. Multiple controllers in the same application can use different groupId values. The same groupId of different applications is automatically isolated. The value range is [OH_TRAFFICFILTER_MIN_GROUP_ID, OH_TRAFFICFILTER_MAX_GROUP_ID]. |
| uint32_t priority | Priority, which determines the execution order among chains with different groupId values. A smaller value indicates a higher execution priority. The value range is [OH_TRAFFICFILTER_MIN_PRIORITY, OH_TRAFFICFILTER_MAX_PRIORITY]. |
| [const OH_TrafficFilter_Config](capi-trafficfilter-oh-trafficfilter-config.md)* config | Configuration parameters. NULL indicates that the default configuration is used. |
| [OH_TrafficFilter_PacketController**](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) controller | Output parameter. On success, it is the packet controller handle. On failure, it is NULL and the handle is unavailable. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission.<br>     [OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - The group_id already exists.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - The group_id or priority is invalid.<br>     [OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - NFQueue initialization failed. |

### OH_TrafficFilter_DestroyPacketController()

```c
int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)
```

**Description**

Destroys a packet controller instance. Destroys the controller instance and releases related resources (including rules). After calling this function, the handle will become invalid.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | Handle to the OH_TrafficFilter_PacketController. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller is NULL.<br>     [OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - The specified controller handle is not found. |

### OH_TrafficFilter_RegisterPacketCallback()

```c
int32_t OH_TrafficFilter_RegisterPacketCallback(
    OH_TrafficFilter_PacketController* controller,
    OH_TrafficFilter_PacketCallback callback,
    void* userData
)
```

**Description**

Registers a packet callback function. Registers a callback function for processing intercepted packets. When a packet matches the filtering rules, the callback is triggered. To release the callback, call OH_TrafficFilter_UnregisterPacketCallback.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | Handle to the OH_TrafficFilter_PacketController. |
| [OH_TrafficFilter_PacketCallback](capi-trafficfilter-oh-trafficfilter-packetcallback.md) callback | Pointer to the callback function. Cannot be NULL. |
| void* userData | User data (returned in the callback). |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller or callback is NULL. |

### OH_TrafficFilter_UnregisterPacketCallback()

```c
int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)
```

**Description**

Unregisters the packet callback function.

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | Handle to the OH_TrafficFilter_PacketController. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller is NULL. |

### OH_TrafficFilter_AddPacketRule()

```c
int32_t OH_TrafficFilter_AddPacketRule(
    OH_TrafficFilter_PacketController* controller,
    const OH_TrafficFilter_FilterRule* rule
)
```

**Description**

Adds a packet filtering rule. The conditions within a single [OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md) struct are in a logical AND relationship. Multiple rules added to the same [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) are in a logical OR relationship. To clear the filtering rules, call [OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule).

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | Handle to the OH_TrafficFilter_PacketController. |
| [const OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md)* rule | Filtering rule. Cannot be NULL. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller or rule is NULL.<br>     [OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - More than 2000 rules are added. |

### OH_TrafficFilter_ClearPacketRule()

```c
int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)
```

**Description**

Clears packet filtering rules (clears all packet filtering rules added to the controller handle).

**Required permissions:** ohos.permission.kernel.TRAFFIC_FILTER

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | Handle of OH_TrafficFilter_PacketController. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Success.<br>     [OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission.<br>     [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - controller is NULL. |
