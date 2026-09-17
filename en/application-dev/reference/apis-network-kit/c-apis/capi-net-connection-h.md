# net_connection.h

## Overview

Provide C interface for the data network connection module of network management.

**Library**: libnet_connection.so

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-netconnection.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_NetConn_HasDefaultNet(int32_t *hasDefaultNet)](#oh_netconn_hasdefaultnet) | Checks whether a default activated data network is available. |
| [int32_t OH_NetConn_GetDefaultNet(NetConn_NetHandle *netHandle)](#oh_netconn_getdefaultnet) | Obtains the default activated data network. |
| [int32_t OH_NetConn_IsDefaultNetMetered(int32_t *isMetered)](#oh_netconn_isdefaultnetmetered) | Checks whether metering is enabled for the default data network. |
| [int32_t OH_NetConn_GetConnectionProperties(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *prop)](#oh_netconn_getconnectionproperties) | Obtains the link information of a data network. |
| [int32_t OH_NetConn_GetNetCapabilities(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities)](#oh_netconn_getnetcapabilities) | Obtains the capabilities of a data network. |
| [int32_t OH_NetConn_GetDefaultHttpProxy(NetConn_HttpProxy *httpProxy)](#oh_netconn_getdefaulthttpproxy) | Obtains the default network proxy. |
| [int32_t OH_NetConn_GetAddrInfo(char *host, char *serv, struct addrinfo *hint, struct addrinfo **res, int32_t netId)](#oh_netconn_getaddrinfo) | Obtains the DNS result based on the specified **netId**. |
| [int32_t OH_NetConn_FreeDnsResult(struct addrinfo *res)](#oh_netconn_freednsresult) | Releases the DNS query result. |
| [int32_t OH_NetConn_GetAllNets(NetConn_NetHandleList *netHandleList)](#oh_netconn_getallnets) | Obtains all activated data networks. |
| [int32_t OHOS_NetConn_RegisterDnsResolver(OH_NetConn_CustomDnsResolver resolver)](#ohos_netconn_registerdnsresolver) | Registers a custom DNS resolver.(Deprecated in API13) |
| [int32_t OHOS_NetConn_UnregisterDnsResolver(void)](#ohos_netconn_unregisterdnsresolver) | Unregisters a custom DNS resolver.(Deprecated in API13) |
| [int32_t OH_NetConn_RegisterDnsResolver(OH_NetConn_CustomDnsResolver resolver)](#oh_netconn_registerdnsresolver) | Registers a custom DNS resolver.(Deprecated in API26.0.0) |
| [int32_t OH_NetConn_UnregisterDnsResolver(void)](#oh_netconn_unregisterdnsresolver) | Unregisters a custom DNS resolver.(Deprecated in API26.0.0) |
| [int32_t OH_NetConn_RegisterCustomDnsResolver(OH_NetConn_CustomDnsResolver resolver)](#oh_netconn_registercustomdnsresolver) | Registers a custom DNS resolver to intercept and override DNS queries. Falls back to system DNS if no result is specified. Only a single resolver is allowed. You must unregister the existing one before registering a new one. |
| [int32_t OH_NetConn_UnregisterCustomDnsResolver(void)](#oh_netconn_unregistercustomdnsresolver) | Unregisters the custom DNS resolver. |
| [int32_t OH_NetConn_BindSocket(int32_t socketFd, NetConn_NetHandle *netHandle)](#oh_netconn_bindsocket) | Binds a socket to the specified network. |
| [int32_t OH_NetConn_SetAppHttpProxy(NetConn_HttpProxy *httpProxy)](#oh_netconn_setapphttpproxy) | Sets an HTTP proxy for the current application. |
| [int32_t OH_NetConn_RegisterAppHttpProxyCallback(OH_NetConn_AppHttpProxyChange appHttpProxyChange, uint32_t *callbackId)](#oh_netconn_registerapphttpproxycallback) | Registers a callback for HTTP proxy changes of the application. |
| [void OH_NetConn_UnregisterAppHttpProxyCallback(uint32_t callbackId)](#oh_netconn_unregisterapphttpproxycallback) | Unregisters the callback for HTTP proxy changes of the application. |
| [int32_t OH_NetConn_RefreshGlobalHttpProxyWithCallback(OH_NetConn_GlobalHttpProxyRefreshCallback callback, void *userContext)](#oh_netconn_refreshglobalhttpproxywithcallback) | Requests global HTTP proxy re-authentication and reports the result through a one-shot callback.<br> This function submits an asynchronous re-authentication request. A return value of 0 indicates that the request has been accepted. It does not indicate that re-authentication has succeeded. The final result is reported through the callback.<br><br> If this function returns 0, the callback will be invoked at most once. After the callback is invoked, it is automatically released by the system.<br><br> If this function returns a non-zero value, the callback will not be invoked.<br><br> The callback may be invoked on a system worker thread. The caller must ensure that the callback implementation is thread-safe and returns quickly.<br><br> The caller must ensure that the callback function and userData remain valid until the callback is invoked. |
| [int32_t OH_NetConn_RegisterNetConnCallback(NetConn_NetSpecifier *specifier, NetConn_NetConnCallback *netConnCallback, uint32_t timeout, uint32_t *callbackId)](#oh_netconn_registernetconncallback) | Registers a callback for network status changes. |
| [int32_t OH_NetConn_RegisterDefaultNetConnCallback(NetConn_NetConnCallback *netConnCallback, uint32_t *callbackId)](#oh_netconn_registerdefaultnetconncallback) | Registers a callback for status changes of the default network. |
| [int32_t OH_NetConn_UnregisterNetConnCallback(uint32_t callBackId)](#oh_netconn_unregisternetconncallback) | Unregisters the callback for network status changes. |
| [NetConn_ErrorCode OH_NetConn_SetPacUrl(const char *pacUrl)](#oh_netconn_setpacurl) | Sets the URL of the system-level Proxy Auto Config (PAC) script, for example, **http://127.0.0.1:21998/ PacProxyScript.pac**. You can obtain the proxy information by parsing the URL. |
| [NetConn_ErrorCode OH_NetConn_GetPacUrl(char *pacUrl)](#oh_netconn_getpacurl) | Obtains the URL of the system-level PAC script. |
| [int32_t OH_NetConn_QueryProbeResult(char *destination, int32_t duration, NetConn_ProbeResultInfo *probeResultInfo)](#oh_netconn_queryproberesult) | Queries network probe results. If an exception (for example, network disconnection) occurs and the request fails to be sent, the API immediately returns the result without performing subsequent detection. This API involves network operations. Do not call it in the main process. Otherwise, the UI may freeze. |
| [int32_t OH_NetConn_QueryTraceRoute(char *destination, NetConn_TraceRouteOption *option, NetConn_TraceRouteInfo *traceRouteInfo)](#oh_netconn_querytraceroute) | Queries network trace route information. |

## Function description

### OH_NetConn_HasDefaultNet()

```c
int32_t OH_NetConn_HasDefaultNet(int32_t *hasDefaultNet)
```

**Description**

Checks whether a default activated data network is available.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t *hasDefaultNet | Whether there is a default network. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_GetDefaultNet()

```c
int32_t OH_NetConn_GetDefaultNet(NetConn_NetHandle *netHandle)
```

**Description**

Obtains the default activated data network.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetConn_NetHandle *netHandle | Network ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_IsDefaultNetMetered()

```c
int32_t OH_NetConn_IsDefaultNetMetered(int32_t *isMetered)
```

**Description**

Checks whether metering is enabled for the default data network.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t *isMetered | Whether metering is enabled. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_GetConnectionProperties()

```c
int32_t OH_NetConn_GetConnectionProperties(NetConn_NetHandle *netHandle, NetConn_ConnectionProperties *prop)
```

**Description**

Obtains the link information of a data network.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetConn_NetHandle *netHandle | Network ID. |
| NetConn_ConnectionProperties *prop | Link information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_GetNetCapabilities()

```c
int32_t OH_NetConn_GetNetCapabilities(NetConn_NetHandle *netHandle, NetConn_NetCapabilities *netCapabilities)
```

**Description**

Obtains the capabilities of a data network.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetConn_NetHandle *netHandle | Network ID. |
| NetConn_NetCapabilities *netCapabilities | Capability set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_GetDefaultHttpProxy()

```c
int32_t OH_NetConn_GetDefaultHttpProxy(NetConn_HttpProxy *httpProxy)
```

**Description**

Obtains the default network proxy.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetConn_HttpProxy *httpProxy | Proxy configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_GetAddrInfo()

```c
int32_t OH_NetConn_GetAddrInfo(char *host, char *serv, struct addrinfo *hint, struct addrinfo **res, int32_t netId)
```

**Description**

Obtains the DNS result based on the specified **netId**.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.INTERNET

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *host | Host name. |
| char *serv | Service name. |
| struct addrinfo *hint | Pointer to the addrinfo structure. |
| struct addrinfo **res | DNS query result, which is in the format of linked lists. |
| int32_t netId | If **netId** is set to **0**, the default **netid** is used for query. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_FreeDnsResult()

```c
int32_t OH_NetConn_FreeDnsResult(struct addrinfo *res)
```

**Description**

Releases the DNS query result.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.INTERNET

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct addrinfo *res | Header of the DNS query result, which is in the format of linked lists. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_GetAllNets()

```c
int32_t OH_NetConn_GetAllNets(NetConn_NetHandleList *netHandleList)
```

**Description**

Obtains all activated data networks.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetConn_NetHandleList *netHandleList | Network information list. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 201: Missing permissions.      <br>401: Parameter error. 2100002: Service connection failure.      <br>2100003: Internal error. |

### OHOS_NetConn_RegisterDnsResolver()

```c
int32_t OHOS_NetConn_RegisterDnsResolver(OH_NetConn_CustomDnsResolver resolver)
```

**Description**

Registers a custom DNS resolver.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Deprecated**: 13

**Replaced by**: OH_NetConn_RegisterDnsResolver

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NetConn_CustomDnsResolver resolver | Pointer to the custom DNS resolver. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success. 401: Parameter error.      <br>2100002: Service connection failure.  2100003: Internal error. |

### OHOS_NetConn_UnregisterDnsResolver()

```c
int32_t OHOS_NetConn_UnregisterDnsResolver(void)
```

**Description**

Unregisters a custom DNS resolver.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Deprecated**: 13

**Replaced by**: OH_NetConn_UnregisterDnsResolver

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_RegisterDnsResolver()

```c
int32_t OH_NetConn_RegisterDnsResolver(OH_NetConn_CustomDnsResolver resolver)
```

**Description**

Registers a custom DNS resolver.

**Since**: 13

**Deprecated**: 26.0.0

**Replaced by**: OH_NetConn_RegisterCustomDnsResolver

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NetConn_CustomDnsResolver resolver | Pointer to the custom DNS resolver. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>NETMANAGER_EXT_SUCCESS: Operation success.      <br>NETMANAGER_ERR_PARAMETER_ERROR: Parameter error. Enter a correct parameter. |

### OH_NetConn_UnregisterDnsResolver()

```c
int32_t OH_NetConn_UnregisterDnsResolver(void)
```

**Description**

Unregisters a custom DNS resolver.

**Since**: 13

**Deprecated**: 26.0.0

**Replaced by**: OH_NetConn_UnregisterCustomDnsResolver

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_RegisterCustomDnsResolver()

```c
int32_t OH_NetConn_RegisterCustomDnsResolver(OH_NetConn_CustomDnsResolver resolver)
```

**Description**

Registers a custom DNS resolver to intercept and override DNS queries. Falls back to system DNS if no result is specified. Only a single resolver is allowed. You must unregister the existing one before registering a new one.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NetConn_CustomDnsResolver resolver | Pointer to the custom DNS resolver. If the resolver returns 0, skip system DNS; otherwise, fallback to system DNS. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 - Success.          401 - Parameter error. Please enter a correct parameter.          2101008 - Resolver already exists. use OH_NetConn_UnregisterCustomDnsResolver before registering a new one. |

### OH_NetConn_UnregisterCustomDnsResolver()

```c
int32_t OH_NetConn_UnregisterCustomDnsResolver(void)
```

**Description**

Unregisters the custom DNS resolver.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 - Success.          2100003 - Internal error. |

### OH_NetConn_BindSocket()

```c
int32_t OH_NetConn_BindSocket(int32_t socketFd, NetConn_NetHandle *netHandle)
```

**Description**

Binds a socket to the specified network.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t socketFd | Socket constructed by the user. |
| NetConn_NetHandle *netHandle | Pointer to the network handle containing the network ID. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>401: Parameter error.      <br>2100002: Service connection failure.      <br>2100003: Internal error. |

### OH_NetConn_SetAppHttpProxy()

```c
int32_t OH_NetConn_SetAppHttpProxy(NetConn_HttpProxy *httpProxy)
```

**Description**

Sets an HTTP proxy for the current application.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| NetConn_HttpProxy *httpProxy | HTTP proxy to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>401: Parameter error. |

### OH_NetConn_RegisterAppHttpProxyCallback()

```c
int32_t OH_NetConn_RegisterAppHttpProxyCallback(OH_NetConn_AppHttpProxyChange appHttpProxyChange, uint32_t *callbackId)
```

**Description**

Registers a callback for HTTP proxy changes of the application.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NetConn_AppHttpProxyChange appHttpProxyChange | Callback to register. |
| uint32_t *callbackId | ID of the registered callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>401: Parameter error. |

### OH_NetConn_UnregisterAppHttpProxyCallback()

```c
void OH_NetConn_UnregisterAppHttpProxyCallback(uint32_t callbackId)
```

**Description**

Unregisters the callback for HTTP proxy changes of the application.

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t callbackId | ID of the callback to unregister. |

### OH_NetConn_RefreshGlobalHttpProxyWithCallback()

```c
int32_t OH_NetConn_RefreshGlobalHttpProxyWithCallback(OH_NetConn_GlobalHttpProxyRefreshCallback callback, void *userContext)
```

**Description**

Requests global HTTP proxy re-authentication and reports the result through a one-shot callback.<br> This function submits an asynchronous re-authentication request. A return value of 0 indicates that the request has been accepted. It does not indicate that re-authentication has succeeded. The final result is reported through the callback.<br><br> If this function returns 0, the callback will be invoked at most once. After the callback is invoked, it is automatically released by the system.<br><br> If this function returns a non-zero value, the callback will not be invoked.<br><br> The callback may be invoked on a system worker thread. The caller must ensure that the callback implementation is thread-safe and returns quickly.<br><br> The caller must ensure that the callback function and userData remain valid until the callback is invoked.

**Required permission**: ohos.permission.INTERNET

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NetConn_GlobalHttpProxyRefreshCallback callback | The one-shot callback used to receive the re-authentication result. It must not be NULL. |
| void *userContext | The user-defined data passed to the callback. It can be NULL. The system does not access, copy, or release it. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>0 - Success.</li>      <li>201 - Permission denied.</li>      <li>401 - Parameter error.</li></ul> |

### OH_NetConn_RegisterNetConnCallback()

```c
int32_t OH_NetConn_RegisterNetConnCallback(NetConn_NetSpecifier *specifier, NetConn_NetConnCallback *netConnCallback, uint32_t timeout, uint32_t *callbackId)
```

**Description**

Registers a callback for network status changes.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| netSpecifier | Network feature set. |
| callback | Registered callbacks. |
| uint32_t timeout | Timeout duration, in milliseconds. The value **0** indicates infinite waiting. |
| uint32_t *callbackId | Callback IDs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions.      <br>401: Parameter error.      <br>2100002: Service connection failure.      <br>2100003: Internal error.      <br>2101008: Callback already registered.      <br>2101022: Maximum number of requests exceeded. |

### OH_NetConn_RegisterDefaultNetConnCallback()

```c
int32_t OH_NetConn_RegisterDefaultNetConnCallback(NetConn_NetConnCallback *netConnCallback, uint32_t *callbackId)
```

**Description**

Registers a callback for status changes of the default network.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| callback | Registered callbacks. |
| uint32_t *callbackId | Callback IDs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions.      <br>401: Parameter error.      <br>2100002: Service connection failure.      <br>2100003: Internal error.      <br>2101008: Callback already registered.      <br>2101022: Maximum number of requests exceeded. |

### OH_NetConn_UnregisterNetConnCallback()

```c
int32_t OH_NetConn_UnregisterNetConnCallback(uint32_t callBackId)
```

**Description**

Unregisters the callback for network status changes.

**System capability**: SystemCapability.Communication.NetManager.Core

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t callBackId | ID of the callback to unregister. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions.      <br>401: Parameter error.      <br>2100002: Service connection failure.      <br>2100003: Internal error.      <br>2101007: Callback not exist. |

### OH_NetConn_SetPacUrl()

```c
NetConn_ErrorCode OH_NetConn_SetPacUrl(const char *pacUrl)
```

**Description**

Sets the URL of the system-level Proxy Auto Config (PAC) script, for example, **http://127.0.0.1:21998/ PacProxyScript.pac**. You can obtain the proxy information by parsing the URL.

**Required permission**: ohos.permission.SET_PAC_URL

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *pacUrl | Address of the PAC script. |

**Returns**:

| Type | Description |
| -- | -- |
| NetConn_ErrorCode | Result code defined in {@link NetConn_ErrorCode}.<br>    <br>{@link NETCONN_SUCCESS}: success.<br>    <br>{@link NETCONN_PERMISSION_DENIED}: permission denied.<br>    <br>{@link NETCONN_PARAMETER_ERROR}: parameter error.<br>    <br>{@link NETCONN_OPERATION_FAILED}: unable to connect to the service.<br>    <br>{@link NETCONN_INTERNAL_ERROR}: internal error. |

### OH_NetConn_GetPacUrl()

```c
NetConn_ErrorCode OH_NetConn_GetPacUrl(char *pacUrl)
```

**Description**

Obtains the URL of the system-level PAC script.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *pacUrl | URL of the PAC script. |

**Returns**:

| Type | Description |
| -- | -- |
| NetConn_ErrorCode | Result code defined in {@link NetConn_ErrorCode}.<br>    <br>{@link NETCONN_SUCCESS}: success.<br>    <br>{@link NETCONN_PARAMETER_ERROR}: parameter error.<br>    <br>{@link NETCONN_OPERATION_FAILED}: unable to connect to the service.<br>    <br>{@link NETCONN_INTERNAL_ERROR}: internal error. |

### OH_NetConn_QueryProbeResult()

```c
int32_t OH_NetConn_QueryProbeResult(char *destination, int32_t duration, NetConn_ProbeResultInfo *probeResultInfo)
```

**Description**

Queries network probe results. If an exception (for example, network disconnection) occurs and the request fails to be sent, the API immediately returns the result without performing subsequent detection. This API involves network operations. Do not call it in the main process. Otherwise, the UI may freeze.

**Required permission**: ohos.permission.INTERNET

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *destination | Target domain name or IP address to be detected. For a domain name, the domain name is resolved to the target IP address before the detection, and then the detection is initiated. The domain name resolution time is not included in the probe duration indicated by duration. |
| int32_t duration | Probe duration. in seconds. The detection interval is 1 second. Therefore, you can use this field to control the number of detections. |
| NetConn_ProbeResultInfo *probeResultInfo | Packet loss rate and round-trip time (RTT). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions.      <br>401: Parameter error.      <br>2100003: Internal error. |

### OH_NetConn_QueryTraceRoute()

```c
int32_t OH_NetConn_QueryTraceRoute(char *destination, NetConn_TraceRouteOption *option, NetConn_TraceRouteInfo *traceRouteInfo)
```

**Description**

Queries network trace route information.

**Required permission**: ohos.permission.INTERNET and ohos.permission.LOCATION and ohos.permission.ACCESS_NET_TRACE_INFO

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *destination | Destination address. |
| NetConn_TraceRouteOption *option | Route options. |
| NetConn_TraceRouteInfo *traceRouteInfo | Route result. An array pointer needs to be passed. The array size indicates the number of route hops, which is **30** by default. If you customize the number of hops, ensure that the array size is the same as the value of **maxJumpNumber** in the **option** field. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions. |


