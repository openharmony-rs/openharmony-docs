# net_trafficfilter.h

## Overview

Declares the C APIs for network traffic filtering and redirection. This header file provides the APIs for creating and destroying a packet controller, registering packet callbacks, adding and clearing filtering rules, as well as creating and destroying a traffic redirector, and adding and clearing redirection rules. <br>It is applicable to scenarios where network packets need to be intercepted, filtered, and redirected at the system level.

**Library**: libnet_trafficfilter.so

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)](#oh_trafficfilter_createredirector) | Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) must be called to release resources. If this function fails, no valid redirector is returned. |
| [int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_destroyredirector) | Destroys the redirection instance and releases related resources (including rules). The handle becomes invalid after the function is called. |
| [int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)](#oh_trafficfilter_addredirectrule) | Adds a TCP traffic redirection rule to redirect matching traffic to the specified proxy server. To delete a redirection rule, call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule). |
| [int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)](#oh_trafficfilter_clearredirectrule) | Clears all redirection rules. |
| [int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)](#oh_trafficfilter_queryprocess) | Queries the process information based on network connection. This function queries the process that starts the connection using the five-tuple connection information, including the source IP address, destination IP address, source port number, destination port number, and protocol type. |
| [int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)](#oh_trafficfilter_addpacketrule) | Adds a packet filter rule. The conditions within a single [OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md) struct are in a logical AND relationship. Multiple rules added to the same [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) are in a logical OR relationship. To clear the filter rules, call [OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule). |
| [int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_clearpacketrule) | Clears packet filter rules (clears all packet filter rules added to the controller handle). |
| [int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)](#oh_trafficfilter_createpacketcontroller) | Creates a packet controller instance. Creates a packet controller for intercepting and filtering network packets Resource Management: This instance occupies system resources. You must call [OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to release resources. If this function fails, no valid controller is returned. |
| [int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_destroypacketcontroller) | Destroys a packet controller instance. Destroys the controller instance and releases related resources (including rules). After the call, the handle becomes invalid. |
| [int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)](#oh_trafficfilter_registerpacketcallback) | Registers a packet callback function. Registers a callback function to process intercepted packets. When a packet matches a filter rule, the callback is triggered. To release the callback, call [OH_TrafficFilter_UnregisterPacketCallback](capi-net-trafficfilter-h.md#oh_trafficfilter_unregisterpacketcallback). |
| [int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)](#oh_trafficfilter_unregisterpacketcallback) | Unregisters the packet callback function. |

## Function description

### OH_TrafficFilter_CreateRedirector()

```c
int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)
```

**Description**

Creates a traffic redirection instance for redirecting TCP traffic to a proxy server. [OH_TrafficFilter_DestroyRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) must be called to release resources. If this function fails, no valid redirector is returned.

<!--Device-int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)--><!--Device-int32_t OH_TrafficFilter_CreateRedirector(uint32_t group_id, uint32_t priority, OH_TrafficFilter_Redirector** redirector)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Resource release**: [OH_TrafficFilter_DestroyRedirector](#oh_trafficfilter_destroyredirector)

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t group_id | Redirection link ID, which is a logical group ID within an app. Different **group_id** values can be used for multiple redirectors within the same app. Redirectors with the same **group_id** in different apps are automatically isolated. The value range is [[OH_TRAFFICFILTER_MIN_GROUP_ID](capi-net-trafficfilter-type-h.md#macros), [OH_TRAFFICFILTER_MAX_GROUP_ID](capi-net-trafficfilter-type-h.md#macros)]. If the value is out of this range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| uint32_t priority | Priority, which determines the execution order among links with different **group_id** values. A smaller value indicates a higher priority. Note: The redirector priority is higher than the packet filter priority. The value range is [[OH_TRAFFICFILTER_MIN_PRIORITY](capi-net-trafficfilter-type-h.md#macros), [OH_TRAFFICFILTER_MAX_PRIORITY](capi-net-trafficfilter-type-h.md#macros)]. If the value is out of range, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)** redirector | Output parameter. On success, it is the double pointer to the redirector handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): group_id already exists.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Invalid parameter.</li> <li>[OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): NFQueue initialization failed.</li></ul> |

### OH_TrafficFilter_DestroyRedirector()

```c
int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Destroys the redirection instance and releases related resources (including rules). The handle becomes invalid after the function is called.

<!--Device-int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)--><!--Device-int32_t OH_TrafficFilter_DestroyRedirector(OH_TrafficFilter_Redirector* redirector)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Pointer to the handle to **OH_TrafficFilter_Redirector**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **redirector** value is **NULL**.</li> <li>[OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The specified redirector handle is not found.</li></ul> |

### OH_TrafficFilter_AddRedirectRule()

```c
int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)
```

**Description**

Adds a TCP traffic redirection rule to redirect matching traffic to the specified proxy server. To delete a redirection rule, call [OH_TrafficFilter_ClearRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule).

<!--Device-int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)--><!--Device-int32_t OH_TrafficFilter_AddRedirectRule(OH_TrafficFilter_Redirector* redirector, const OH_TrafficFilter_RedirectRule* rule)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Pointer to the handle to **OH_TrafficFilter_Redirector**. |
| [const OH_TrafficFilter_RedirectRule](capi-trafficfilter-oh-trafficfilter-redirectrule.md)* rule | Pointer to the redirection rule. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **redirector** or **rule** value is **NULL**.</li> <li>[OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Too many rules added.</li></ul> |

### OH_TrafficFilter_ClearRedirectRule()

```c
int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)
```

**Description**

Clears all redirection rules.

<!--Device-int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)--><!--Device-int32_t OH_TrafficFilter_ClearRedirectRule(OH_TrafficFilter_Redirector* redirector)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md)* redirector | Pointer to the handle to **OH_TrafficFilter_Redirector**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The **redirector** value is NULL.</li></ul> |

### OH_TrafficFilter_QueryProcess()

```c
int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)
```

**Description**

Queries the process information based on network connection. This function queries the process that starts the connection using the five-tuple connection information, including the source IP address, destination IP address, source port number, destination port number, and protocol type.

<!--Device-int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)--><!--Device-int32_t OH_TrafficFilter_QueryProcess(const OH_TrafficFilter_ConnectionInfo* connection_info, OH_TrafficFilter_ProcessInfo* process_info)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)* connection_info | Pointer to the input connection information. |
| [OH_TrafficFilter_ProcessInfo](capi-trafficfilter-oh-trafficfilter-processinfo.md)* process_info | Pointer to the output process information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Invalid parameter.</li> <li>[OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Process not found.</li></ul> |

### OH_TrafficFilter_AddPacketRule()

```c
int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)
```

**Description**

Adds a packet filter rule. The conditions within a single [OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md) struct are in a logical AND relationship. Multiple rules added to the same [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) are in a logical OR relationship. To clear the filter rules, call [OH_TrafficFilter_ClearPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule).

<!--Device-int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)--><!--Device-int32_t OH_TrafficFilter_AddPacketRule(OH_TrafficFilter_PacketController* controller, const OH_TrafficFilter_FilterRule* rule)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | [in] Pointer to the handle to the **OH_TrafficFilter_PacketController**. |
| [const OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md)* rule | [in] Filter rule. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): **controller** or **rule** is NULL.</li> <li>[OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): More than 2000 rules are added.</li></ul> |

### OH_TrafficFilter_ClearPacketRule()

```c
int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)
```

**Description**

Clears packet filter rules (clears all packet filter rules added to the controller handle).

<!--Device-int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)--><!--Device-int32_t OH_TrafficFilter_ClearPacketRule(OH_TrafficFilter_PacketController* controller)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | [in] Pointer to the handle to **OH_TrafficFilter_PacketController**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): **controller** is NULL.</li></ul> |

### OH_TrafficFilter_CreatePacketController()

```c
int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)
```

**Description**

Creates a packet controller instance. Creates a packet controller for intercepting and filtering network packets Resource Management: This instance occupies system resources. You must call [OH_TrafficFilter_DestroyPacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to release resources. If this function fails, no valid controller is returned.

<!--Device-int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)--><!--Device-int32_t OH_TrafficFilter_CreatePacketController(uint32_t groupId, uint32_t priority, const OH_TrafficFilter_Config* config, OH_TrafficFilter_PacketController** controller)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Resource release**: [OH_TrafficFilter_DestroyPacketController](#oh_trafficfilter_destroypacketcontroller)

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t groupId | [in] Filter chain identifier. This is the logical group ID within the application. Multiple controllers in the same application can use different groupIds. The same group ID of different applications is automatically isolated. |
| uint32_t priority | [in] Priority(Determine the execution sequence of different groupId chains. The smaller the value, the earlier the execution.) |
| [const OH_TrafficFilter_Config](capi-trafficfilter-oh-trafficfilter-config.md)* config | [in] Configuration parameters (can be NULL to use default configuration) |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)** controller | [out] Output parameter, <ul><li>the packet controller handle on success.</li></ul> |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - succeeded.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - Missing permission. </li> <li>[OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - The groupId already exists. </li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - The priority is invalid. </li> <li>[OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode) - NFQueue initialization failed. </li></ul> |

### OH_TrafficFilter_DestroyPacketController()

```c
int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)
```

**Description**

Destroys a packet controller instance. Destroys the controller instance and releases related resources (including rules). After the call, the handle becomes invalid.

<!--Device-int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)--><!--Device-int32_t OH_TrafficFilter_DestroyPacketController(OH_TrafficFilter_PacketController* controller)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | [in] Pointer to the **OH_TrafficFilter_PacketController** handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): **controller** is NULL.</li> <li>[OH_TRAFFICFILTER_ERROR_NOT_FOUND](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): The specified controller handle is not found.</li></ul> |

### OH_TrafficFilter_RegisterPacketCallback()

```c
int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)
```

**Description**

Registers a packet callback function. Registers a callback function to process intercepted packets. When a packet matches a filter rule, the callback is triggered. To release the callback, call [OH_TrafficFilter_UnregisterPacketCallback](capi-net-trafficfilter-h.md#oh_trafficfilter_unregisterpacketcallback).

<!--Device-int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)--><!--Device-int32_t OH_TrafficFilter_RegisterPacketCallback(OH_TrafficFilter_PacketController* controller, OH_TrafficFilter_PacketCallback callback, void* userData)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | [in] Pointer to the handle to the **OH_TrafficFilter_PacketController**. |
| [OH_TrafficFilter_PacketCallback](capi-net-trafficfilter-type-h.md#oh_trafficfilter_packetcallback) callback | [in] Callback function pointer. Cannot be NULL. |
| void* userData | [in] Pointer to the user data (returned in the callback). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): **controller** or **callback** is NULL.</li></ul> |

### OH_TrafficFilter_UnregisterPacketCallback()

```c
int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)
```

**Description**

Unregisters the packet callback function.

<!--Device-int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)--><!--Device-int32_t OH_TrafficFilter_UnregisterPacketCallback(OH_TrafficFilter_PacketController* controller)-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Required permission**: ohos.permission.kernel.TRAFFIC_FILTER

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md)* controller | [in] Pointer to the handle to the **OH_TrafficFilter_PacketController**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Success.</li> <li>[OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): Permission denied.</li> <li>[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode): **controller** is NULL.</li></ul> |


