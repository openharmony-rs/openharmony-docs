# net_http.h

## Overview

Defines the APIs of the HTTP request module.

**Library**: libnet_http.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [Http_Headers *OH_Http_CreateHeaders(void)](#oh_http_createheaders) | Creates an HTTP request or response header.<br> > **NOTE**<br>> > You are advised to call [OH_Http_DestroyHeaders](capi-net-http-h.md#oh_http_destroyheaders) to destroy the HTTP request or response header and clear > resources after the HTTP request is complete. |
| [void OH_Http_DestroyHeaders(Http_Headers **headers)](#oh_http_destroyheaders) | Destroys an HTTP request or response header. |
| [uint32_t OH_Http_SetHeaderValue(struct Http_Headers *headers, const char *name, const char *value)](#oh_http_setheadervalue) | Sets the key-value pairs of an HTTP request or response header. |
| [Http_HeaderValue *OH_Http_GetHeaderValue(Http_Headers *headers, const char *name)](#oh_http_getheadervalue) | Obtains the value of an HTTP request or response header based on the specified key. |
| [Http_HeaderEntry *OH_Http_GetHeaderEntries(Http_Headers *headers)](#oh_http_getheaderentries) | Obtains all key-value pairs from an HTTP request or response header. |
| [void OH_Http_DestroyHeaderEntries(Http_HeaderEntry **headerEntry)](#oh_http_destroyheaderentries) | Destroys all key-value pairs obtained from **OH_Http_GetHeaderEntries**. |
| [Http_Request *OH_Http_CreateRequest(const char *url)](#oh_http_createrequest) | Creates an HTTP request. |
| [int OH_Http_Request(Http_Request *request, Http_ResponseCallback callback, Http_EventsHandler handler)](#oh_http_request) | Initiates an HTTP request.<br> > **NOTE**<br>> > You are advised to call [OH_Http_Destroy](capi-net-http-h.md#oh_http_destroy) to interrupt the HTTP request after the HTTP request receives a > response and the response is processed. |
| [void OH_Http_Destroy(struct Http_Request **request)](#oh_http_destroy) | Stops the HTTP request. |

## Function description

### OH_Http_CreateHeaders()

```c
Http_Headers *OH_Http_CreateHeaders(void)
```

**Description**

Creates an HTTP request or response header.<br>
> **NOTE**
>
> You are advised to call [OH_Http_DestroyHeaders](capi-net-http-h.md#oh_http_destroyheaders) to destroy the HTTP request or response header and clear
> resources after the HTTP request is complete.

<!--Device-Http_Headers *OH_Http_CreateHeaders(void)--><!--Device-Http_Headers *OH_Http_CreateHeaders(void)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [Http_Headers *](capi-netstack-http-headers.md) | Pointer to the HTTP request or response header. |

### OH_Http_DestroyHeaders()

```c
void OH_Http_DestroyHeaders(Http_Headers **headers)
```

**Description**

Destroys an HTTP request or response header.

<!--Device-void OH_Http_DestroyHeaders(Http_Headers **headers)--><!--Device-void OH_Http_DestroyHeaders(Http_Headers **headers)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Http_Headers](capi-netstack-http-headers.md) **headers | HTTP request or response header to be destroyed. The header is generated using **OH_Http_CreateHeaders**. |

### OH_Http_SetHeaderValue()

```c
uint32_t OH_Http_SetHeaderValue(struct Http_Headers *headers, const char *name, const char *value)
```

**Description**

Sets the key-value pairs of an HTTP request or response header.

<!--Device-uint32_t OH_Http_SetHeaderValue(struct Http_Headers *headers, const char *name, const char *value)--><!--Device-uint32_t OH_Http_SetHeaderValue(struct Http_Headers *headers, const char *name, const char *value)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to **Http_Headers**. |
| const char *name | Key name. |
| const char *value | Key value. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | A status code of the uint32_t type. <ul><li>**0**: Success.</li> <li>**401**: Invalid parameter.</li> <li>**2300027**: Insufficient memory.</li></ul> |

### OH_Http_GetHeaderValue()

```c
Http_HeaderValue *OH_Http_GetHeaderValue(Http_Headers *headers, const char *name)
```

**Description**

Obtains the value of an HTTP request or response header based on the specified key.

<!--Device-Http_HeaderValue *OH_Http_GetHeaderValue(Http_Headers *headers, const char *name)--><!--Device-Http_HeaderValue *OH_Http_GetHeaderValue(Http_Headers *headers, const char *name)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to [Http_Headers](capi-netstack-http-headers.md). |
| const char *name | Key name. |

**Returns**:

| Type | Description |
| -- | -- |
| [Http_HeaderValue *](capi-netstack-http-headervalue.md) | Pointer to **Http_HeaderValue**. |

### OH_Http_GetHeaderEntries()

```c
Http_HeaderEntry *OH_Http_GetHeaderEntries(Http_Headers *headers)
```

**Description**

Obtains all key-value pairs from an HTTP request or response header.

<!--Device-Http_HeaderEntry *OH_Http_GetHeaderEntries(Http_Headers *headers)--><!--Device-Http_HeaderEntry *OH_Http_GetHeaderEntries(Http_Headers *headers)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to [Http_Headers](capi-netstack-http-headers.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [Http_HeaderEntry *](capi-netstack-http-headerentry.md) | Pointer to **Http_HeaderEntry**. |

### OH_Http_DestroyHeaderEntries()

```c
void OH_Http_DestroyHeaderEntries(Http_HeaderEntry **headerEntry)
```

**Description**

Destroys all key-value pairs obtained from **OH_Http_GetHeaderEntries**.

<!--Device-void OH_Http_DestroyHeaderEntries(Http_HeaderEntry **headerEntry)--><!--Device-void OH_Http_DestroyHeaderEntries(Http_HeaderEntry **headerEntry)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Http_HeaderEntry](capi-netstack-http-headerentry.md) **headerEntry | Pointer to **Http_HeaderEntry**, which is obtained through **OH_Http_GetHeaderEntries**. |

### OH_Http_CreateRequest()

```c
Http_Request *OH_Http_CreateRequest(const char *url)
```

**Description**

Creates an HTTP request.

<!--Device-Http_Request *OH_Http_CreateRequest(const char *url)--><!--Device-Http_Request *OH_Http_CreateRequest(const char *url)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *url | Request URL. |

**Returns**:

| Type | Description |
| -- | -- |
| [Http_Request *](capi-netstack-http-request.md) | Pointer to **Http_Request**. |

### OH_Http_Request()

```c
int OH_Http_Request(Http_Request *request, Http_ResponseCallback callback, Http_EventsHandler handler)
```

**Description**

Initiates an HTTP request.<br>
> **NOTE**
>
> You are advised to call [OH_Http_Destroy](capi-net-http-h.md#oh_http_destroy) to interrupt the HTTP request after the HTTP request receives a
> response and the response is processed.

<!--Device-int OH_Http_Request(Http_Request *request, Http_ResponseCallback callback, Http_EventsHandler handler)--><!--Device-int OH_Http_Request(Http_Request *request, Http_ResponseCallback callback, Http_EventsHandler handler)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Required permission**: ohos.permission.INTERNET

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Http_Request](capi-netstack-http-request.md) *request | Pointer to [Http_Request](capi-netstack-http-request.md). |
| [Http_ResponseCallback](capi-net-http-type-h.md#http_responsecallback) callback | HTTP response callback. |
| [Http_EventsHandler](capi-netstack-http-eventshandler.md) handler | HTTP event handler. |

**Returns**:

| Type | Description |
| -- | -- |
| int | **0** if the operation is successful; an error code otherwise. For details about the error code description, see **Http_ErrCode**.<br>**Http_ResponseCallback** also carries **errCode**, indicating that the operation is successful but server communication is abnormal due to some reasons. For details, see **Http_ErrCode**. |

### OH_Http_Destroy()

```c
void OH_Http_Destroy(struct Http_Request **request)
```

**Description**

Stops the HTTP request.

<!--Device-void OH_Http_Destroy(struct Http_Request **request)--><!--Device-void OH_Http_Destroy(struct Http_Request **request)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct Http_Request](capi-netstack-http-request.md) **request | Pointer to the request to be interrupted, which is a pointer to **Http_Request**. For details, see [Http_Request](capi-netstack-http-request.md). |


