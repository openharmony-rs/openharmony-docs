# net_trafficfilter.h

## Overview

Declares the C APIs for network traffic filtering and redirection. This header file provides APIs for creating and destroying a packet controller, registering packet callbacks, adding and deleting filtering rules, creating and destroying a traffic redirector, and adding and deleting redirection rules. <br>It is applicable to scenarios where network packets need to be intercepted, filtered, and redirected at the system level.

**Library**: libnet_trafficfilter.so

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)](#oh_trafficfilter_createredirector) | Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) must be called to release resources. If this function fails, no valid redirector is returned. |
| [int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_destroyredirector) | Destroys the redirection instance and releases related resources (including rules). The handle becomes invalid after the function is called. |
| [int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)](#oh_trafficfilter_addredirectrule) | Adds a redirection rule Adds a TCP traffic redirection rule to redirect matched traffic to specified proxy server To clear redirect rules, you need to call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule). |
| [int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_clearredirectrule) | Clears all redirection rules. |
| [int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)](#oh_trafficfilter_queryprocess) | Queries the process information based on network connection. This function queries the process that starts the connection using the five-tuple connection information, including the source IP address, destination IP address, source port number, destination port number, and protocol type. |
| [int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)](#oh_trafficfilter_addpacketrule) | Set packet filter rule Add a packet filter rule to controller chain. only packets matching the rule will be intercepted and sent to callback function. |
| [int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_clearpacketrule) | Clear packet filter rule Clear all packet filter rules in controller. |
| [int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)](#oh_trafficfilter_createpacketcontroller) | Creates a packet controller instance. Creates a packet controller for intercepting and filtering network packets Resource Management: This instance occupies system resources. You must call [OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to release resources. If this function fails, no valid controller is returned. |
| [int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_destroypacketcontroller) | Destroys a packet controller instance. Destroys the controller and releases related resources, including rules and callbacks. After calling this function, the handle is invalid. Do not use it again. |
| [int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)](#oh_trafficfilter_registerpacketcallback) | Register a packet callback function. Register a callback function to handle intercepted packets. The callback will be triggered when packets match the filter rule. |
| [int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_unregisterpacketcallback) | Unregister a packet callback function. Unregister the current packet callback function. After calling this, no more packets will be delivered to the callback. |

## Function description

### OH_TrafficFilter_CreateRedirector()

```c
int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)
```

**Description**

Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) must be called to release resources. If this function fails, no valid redirector is returned.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t group_id | Redirection link ID, which is a logical group ID within an app. Different **group_id** values can be used for multiple redirectors within the same app. Redirectors with the same **group_id** in different apps are automatically isolated. The value range is [[OH_TRAFFICFILTER_MIN_GROUP_ID](capi-net-trafficfilter-type-h.md#宏定义), [OH_TRAFFICFILTER_MAX_GROUP_ID](capi-net-trafficfilter-type-h.md#宏定义)]. If the value is out of this range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| uint32_t priority | Priority, which determines the execution order among links with different **group_id** values. A smaller value indicates a higher priority. Note: The redirector priority is higher than the packet filter priority. The value range is [[OH_TRAFFICFILTER_MIN_PRIORITY](capi-net-trafficfilter-type-h.md#宏定义), [OH_TRAFFICFILTER_MAX_PRIORITY](capi-net-trafficfilter-type-h.md#宏定义)]. If the value is out of range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| OH_TrafficFilter_Redirector** redirector | Output parameter, which is the redirection handle when the operation is successful. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.      <br>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.      <br>[OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The group_id exists.      <br>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Parameter error. |

### OH_TrafficFilter_DestroyRedirector()

```c
int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Destroys the redirection instance and releases related resources (including rules). The handle becomes invalid after the function is called.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_Redirector* redirector | Handle of **OH_TrafficFilter_Redirector**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.      <br>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.      <br>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The redirector value is NULL.      <br>[OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The specified redirector handle is not found. |

### OH_TrafficFilter_AddRedirectRule()

```c
int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)
```

**Description**

Adds a redirection rule Adds a TCP traffic redirection rule to redirect matched traffic to specified proxy server To clear redirect rules, you need to call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule).

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_Redirector* redirector | OH_TrafficFilter_Redirector handle |
| const OH_TrafficFilter_RedirectRule* rule | Redirection rule. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if redirector or rule is NULL.</li>      <li>[OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if too many rules added.</li></ul> |

### OH_TrafficFilter_ClearRedirectRule()

```c
int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Clears all redirection rules.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_Redirector* redirector | Handle of **OH_TrafficFilter_Redirector**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.      <br>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.      <br>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The redirector value is NULL. |

### OH_TrafficFilter_QueryProcess()

```c
int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)
```

**Description**

Queries the process information based on network connection. This function queries the process that starts the connection using the five-tuple connection information, including the source IP address, destination IP address, source port number, destination port number, and protocol type.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_TrafficFilter_ConnectionInfo* connection_info | Input connection information. |
| OH_TrafficFilter_ProcessInfo* process_info | Output process information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.      <br>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Missing permissions.      <br>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Invalid input parameter.      <br>[OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Process not found. |

### OH_TrafficFilter_AddPacketRule()

```c
int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)
```

**Description**

Set packet filter rule Add a packet filter rule to controller chain. only packets matching the rule will be intercepted and sent to callback function.

> **Note**:
>
> Logical relationship: - Conditions within a single OH_TrafficFilter_FilterRule structure are combined with logical AND. - Multiple rules added to the same OH_TrafficFilter_PacketController are combined with logical OR. To clear filter rules, you need to call [OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule).

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_PacketController* controller | [in] OH_TrafficFilter_PacketController handle |
| const OH_TrafficFilter_FilterRule* rule | [in] Filter rule. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if controller or rule is NULL.</li>      <li>[OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if too many rules added.</li></ul> |

### OH_TrafficFilter_ClearPacketRule()

```c
int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)
```

**Description**

Clear packet filter rule Clear all packet filter rules in controller.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_PacketController* controller | [in] OH_TrafficFilter_PacketController handle |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if controller is NULL.</li></ul> |

### OH_TrafficFilter_CreatePacketController()

```c
int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)
```

**Description**

Creates a packet controller instance. Creates a packet controller for intercepting and filtering network packets Resource Management: This instance occupies system resources. You must call [OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to release resources. If this function fails, no valid controller is returned.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t groupId | [in] Filter chain identifier. This is the logical grouping ID within the application. Multiple controllers within the same application can use different group_id. The same group_id from different applications will be automatically isolated. |
| uint32_t priority | [in] Priority (determines execution order between different group_id chain, smaller number executes first) |
| const OH_TrafficFilter_Config* config | [in] Configuration parameters (can be NULL to use default configuration) |
| OH_TrafficFilter_PacketController** controller | [out] Output parameter, <ul><li>the packet controller handle on success.</li></ul> |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) when group_id already exists.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if priority is invalid.</li>      <li>[OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if NFQueue initialization fails.</li></ul> |

### OH_TrafficFilter_DestroyPacketController()

```c
int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)
```

**Description**

Destroys a packet controller instance. Destroys the controller and releases related resources, including rules and callbacks. After calling this function, the handle is invalid. Do not use it again.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_PacketController* controller | [in] OH_TrafficFilter_PacketController handle |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if controller is NULL.</li>      <li>[OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if the specified controller handle is not found.</li></ul> |

### OH_TrafficFilter_RegisterPacketCallback()

```c
int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)
```

**Description**

Register a packet callback function. Register a callback function to handle intercepted packets. The callback will be triggered when packets match the filter rule.

> **Note**:
>
> <strong>Callback Model:</strong> <ul> <li><strong>Single Slot Model:</strong> A single <code>controller</code> instance supports only one active callback at a time.</li> <li><strong>Repeated Registration:</strong> If called again with a non-NULL callback, the new callback <strong>replaces</strong> the previously registered one. The previous callback is immediately unregistered. No error is returned for repeated registration.</li> <li><strong>Unregister/Destroy Semantics:</strong> <ul> <li>Calling [OH_TrafficFilter_UnregisterPacketCallback](capi-net-trafficfilter-h.md#oh_trafficfilter_unregisterpacketcallback) or destroying the <code>controller</code> immediately stops delivery of new packets to the callback.</li> <li><strong>No In-Flight Callbacks:</strong> Once unregistered or destroyed, the framework guarantees that no further callback invocations will occur for that registration, even if packet processing is in progress at the moment of unregistration.</li> </ul> </li> <li><strong>Callback Execution Constraints:</strong> <ul> <li><strong>User Data Lifetime:</strong> The <code>user_data</code> must remain valid from registration until after the callback is unregistered and all ongoing callback invocations have returned.</li> <li><strong>Thread Context:</strong> The callback may be invoked on any thread. Callers must ensure thread safety for shared resources.</li> <li><strong>Ordering and Concurrency:</strong> Callbacks are not guaranteed to be serialized or preserve packet order. Multiple callbacks may be invoked concurrently.</li> <li><strong>Reentrancy:</strong> The callback must not call any <code>OH_TrafficFilter_*</code> registration, unregistration, or controller destruction functions, as this may cause deadlock or undefined behavior.</li> </ul> </li> </ul>

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_PacketController* controller | [in] OH_TrafficFilter_PacketController handle. Must not be NULL. |
| OH_TrafficFilter_PacketCallback callback | [in] Callback function pointer. Cannot be NULL. |
| void* userData | [in] User data (will be passed back in callback). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if controller or callback is NULL.</li></ul> |

### OH_TrafficFilter_UnregisterPacketCallback()

```c
int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)
```

**Description**

Unregister a packet callback function. Unregister the current packet callback function. After calling this, no more packets will be delivered to the callback.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_TrafficFilter_PacketController* controller | [in] OH_TrafficFilter_PacketController handle |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) on success.</li>      <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if permission is denied.</li>      <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) if controller is NULL.</li></ul> |


