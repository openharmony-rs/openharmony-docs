# net_http.h

## Overview

Defines the APIs of the HTTP request module.

**Library**: libnet_http.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [Http_Headers *OH_Http_CreateHeaders(void)](#oh_http_createheaders) | Creates headers for a request or response. |
| [void OH_Http_DestroyHeaders(Http_Headers **headers)](#oh_http_destroyheaders) | Destroys the headers of a request or response. |
| [uint32_t OH_Http_SetHeaderValue(struct Http_Headers *headers, const char *name, const char *value)](#oh_http_setheadervalue) | Sets the key-value pair of the request or response header. |
| [Http_HeaderValue *OH_Http_GetHeaderValue(Http_Headers *headers, const char *name)](#oh_http_getheadervalue) | Obtains the value of a request or response header by key. |
| [Http_HeaderEntry *OH_Http_GetHeaderEntries(Http_Headers *headers)](#oh_http_getheaderentries) | Obtains all the key-value pairs of a request or response header. |
| [void OH_Http_DestroyHeaderEntries(Http_HeaderEntry **headerEntry)](#oh_http_destroyheaderentries) | Destroys all key-value pairs obtained in [OH_Http_GetHeaderEntries](capi-net-http-h.md#oh_http_getheaderentries). |
| [Http_Request *OH_Http_CreateRequest(const char *url)](#oh_http_createrequest) | Create a http request. |
| [int OH_Http_Request(Http_Request *request, Http_ResponseCallback callback, Http_EventsHandler handler)](#oh_http_request) | Initiates an HTTP request. |
| [void OH_Http_Destroy(struct Http_Request **request)](#oh_http_destroy) | Destroy the HTTP request. |

## Function description

### OH_Http_CreateHeaders()

```c
Http_Headers *OH_Http_CreateHeaders(void)
```

**Description**

Creates headers for a request or response.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| Http_Headers * | Http_Headers Pointer to {@link Http_Headers}. |

### OH_Http_DestroyHeaders()

```c
void OH_Http_DestroyHeaders(Http_Headers **headers)
```

**Description**

Destroys the headers of a request or response.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Http_Headers **headers | Pointer to the {@link Http_Headers} to be destroyed, headers ends with null. |

### OH_Http_SetHeaderValue()

```c
uint32_t OH_Http_SetHeaderValue(struct Http_Headers *headers, const char *name, const char *value)
```

**Description**

Sets the key-value pair of the request or response header.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct Http_Headers *headers | Pointer to the {@link Http_Headers} to be set. |
| const char *name | Key. |
| const char *value | Value. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | uint32_t 0 - success. 401 - Parameter error. 2300027 - Out of memory. |

### OH_Http_GetHeaderValue()

```c
Http_HeaderValue *OH_Http_GetHeaderValue(Http_Headers *headers, const char *name)
```

**Description**

Obtains the value of a request or response header by key.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Http_Headers *headers | Pointer to {@link Http_Headers}. |
| const char *name | Key. |

**Returns**:

| Type | Description |
| -- | -- |
| Http_HeaderValue * | Http_HeaderValue Pointer to the obtained {@link Http_HeaderValue}. |

### OH_Http_GetHeaderEntries()

```c
Http_HeaderEntry *OH_Http_GetHeaderEntries(Http_Headers *headers)
```

**Description**

Obtains all the key-value pairs of a request or response header.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Http_Headers *headers | Pointer to {@link Http_Headersaders}. |

**Returns**:

| Type | Description |
| -- | -- |
| Http_HeaderEntry * | Http_HeaderEntry Pointers to all obtained key-value pairs {@link Http_HeaderEntry}. |

### OH_Http_DestroyHeaderEntries()

```c
void OH_Http_DestroyHeaderEntries(Http_HeaderEntry **headerEntry)
```

**Description**

Destroys all key-value pairs obtained in [OH_Http_GetHeaderEntries](capi-net-http-h.md#oh_http_getheaderentries).

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Http_HeaderEntry **headerEntry | Pointer to the {@link Http_HeaderEntry} to be destroyed, headerEntry ends with null. |

### OH_Http_CreateRequest()

```c
Http_Request *OH_Http_CreateRequest(const char *url)
```

**Description**

Create a http request.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *url | Http request url. |

**Returns**:

| Type | Description |
| -- | -- |
| Http_Request * | Pointer of HttpRequest if success; Null otherwise. |

### OH_Http_Request()

```c
int OH_Http_Request(Http_Request *request, Http_ResponseCallback callback, Http_EventsHandler handler)
```

**Description**

Initiates an HTTP request.

**System capability**: SystemCapability.Communication.NetStack

**Required permission**: ohos.permission.INTERNET

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Http_Request *request | Pointer to {@link Http_Request}. |
| Http_ResponseCallback callback | Http response info, pointer to {@link Http_ResponseCallback} |
| Http_EventsHandler handler | Callbacks to watch different events, pointer to {@link Http_EventsHandler}. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if success; non-0 otherwise. For details about error codes, see {@link Http_ErrCode}. |

### OH_Http_Destroy()

```c
void OH_Http_Destroy(struct Http_Request **request)
```

**Description**

Destroy the HTTP request.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct Http_Request **request | Pointer to the http request {@link Http_Request}. |


