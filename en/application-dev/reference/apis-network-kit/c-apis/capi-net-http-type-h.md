# net_http_type.h

## Overview

Defines the data structures for the C APIs of the HTTP request module.

**Library**: libnet_http.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) | Http_Buffer | Defines the HTTP buffer structure. |
| [Http_HeaderValue](capi-netstack-http-headervalue.md) | Http_HeaderValue | Defines the type of a mapped value in a request or response header. |
| [Http_HeaderEntry](capi-netstack-http-headerentry.md) | Http_HeaderEntry | Defines all key-value pairs in the request or response header. |
| [Http_ClientCert](capi-netstack-http-clientcert.md) | Http_ClientCert | Defines the client certificate sent to a remote server, which will be used by the server to verify the identity of the client. |
| [Http_CustomProxy](capi-netstack-http-customproxy.md) | Http_CustomProxy | Defines the custom proxy configuration. |
| [Http_Proxy](capi-netstack-http-proxy.md) | Http_Proxy | Defines the proxy configuration structure. |
| [Http_PerformanceTiming](capi-netstack-http-performancetiming.md) | Http_PerformanceTiming | Defines the HTTP response timing information, which will be collected via {@link Http_Response}. |
| [Http_RequestOptions](capi-netstack-http-requestoptions.md) | Http_RequestOptions | Defines the structure of HTTP requests. |
| [Http_Response](capi-netstack-http-response.md) | Http_Response | Defines the structure of HTTP responses. |
| [Http_Request](capi-netstack-http-request.md) | Http_Request | Defines an HTTP request. |
| [Http_EventsHandler](capi-netstack-http-eventshandler.md) | Http_EventsHandler | Defines the callback for various HTTP events. |
| [Http_Headers](capi-netstack-http-headers.md) | Http_Headers | Defines the header of an HTTP request or response. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Http_ErrCode](#http_errcode) | Http_ErrCode | Defines http error code. |
| [Http_ResponseCode](#http_responsecode) | Http_ResponseCode | Defines http response code. |
| [Http_AddressFamilyType](#http_addressfamilytype) | Http_AddressFamilyType | Defines the address Family. |
| [Http_HttpProtocol](#http_httpprotocol) | Http_HttpProtocol | Defines the HTTP version. |
| [Http_CertType](#http_certtype) | Http_CertType | Defines the Cert Type. |
| [Http_ProxyType](#http_proxytype) | Http_ProxyType | Proxy type. Used to distinguish different proxy configurations. |

### Macro

| Name | Description |
| -- | -- |
| OHOS_HTTP_MAX_PATH_LEN 128 | Defines the maximum path length of an HTTP request.<br>**Since**: 20 |
| OHOS_HTTP_MAX_STR_LEN 256 | Defines the maximum string length of an HTTP request.<br>**Since**: 20 |
| OHOS_HTTP_DNS_SERVER_NUM_MAX 3 | Defines the maximum number of DNS servers for an HTTP request.<br>**Since**: 20 |
| NET_HTTP_METHOD_GET "GET" | Sets the HTTP request method to GET.<br>**Since**: 20 |
| NET_HTTPMETHOD_HEAD "HEAD" | Sets the HTTP request method to HEAD.<br>**Since**: 20 |
| NET_HTTPMETHOD_OPTIONS "OPTIONS" | Sets the HTTP request method to OPTIONS.<br>**Since**: 20 |
| NET_HTTPMETHOD_TRACE "TRACE" | Sets the HTTP request method to TRACE.<br>**Since**: 20 |
| NET_HTTPMETHOD_DELETE "DELETE" | Sets the HTTP request method to DELETE.<br>**Since**: 20 |
| NET_HTTP_METHOD_POST "POST" | Sets the HTTP request method to POST.<br>**Since**: 20 |
| NET_HTTP_METHOD_PUT "PUT" | Sets the HTTP request method to PUT.<br>**Since**: 20 |
| NET_HTTP_METHOD_PATCH "CONNECT" | Sets the HTTP request method to CONNECT.<br>**Since**: 20 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*Http_ResponseCallback)(struct Http_Response *response, uint32_t errCode)](#http_responsecallback) | Http_ResponseCallback | Callback function that is invoked when response is received. |
| [typedef void (\*Http_OnDataReceiveCallback)(const char *data, size_t length)](#http_ondatareceivecallback) | Http_OnDataReceiveCallback | Callback function that is invoked when a response body is received. |
| [typedef void (\*Http_OnProgressCallback)(uint64_t totalSize, uint64_t transferredSize)](#http_onprogresscallback) | Http_OnProgressCallback | Callback function invoked during request/response data transmission. |
| [typedef void (\*Http_OnHeaderReceiveCallback)(Http_Headers *headers)](#http_onheaderreceivecallback) | Http_OnHeaderReceiveCallback | Callback called when header are received. |
| [typedef void (\*Http_OnVoidCallback)(void)](#http_onvoidcallback) | Http_OnVoidCallback | Empty callback function for requested DataEnd or Canceled event callback. |

### Variable

| Name | Description |
| -- | -- |
| void (*Http_ResponseCallback)(struct Http_Response *response, uint32_t errCode) | Callback function that is invoked when response is received.<br>**Since**: 20 |
| void (*Http_OnDataReceiveCallback)(const char *data, size_t length) | Callback function that is invoked when a response body is received.<br>**Since**: 20 |
| void (*Http_OnProgressCallback)(uint64_t totalSize, uint64_t transferredSize) | Callback function invoked during request/response data transmission.<br>**Since**: 20 |
| void (*Http_OnHeaderReceiveCallback)(Http_Headers *headers) | Callback called when header are received.<br>**Since**: 20 |
| void (*Http_OnVoidCallback)(void) | Empty callback function for requested DataEnd or Canceled event callback.<br>**Since**: 20 |

## Enum type description

### Http_ErrCode

```c
enum Http_ErrCode
```

**Description**

Defines http error code.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_HTTP_RESULT_OK = 0 | Operation success. |
| OH_HTTP_PARAMETER_ERROR = 401 | @brief Parameter error. |
| OH_HTTP_PERMISSION_DENIED = 201 | @brief Permission denied. |
| OH_HTTP_NETSTACK_E_BASE = 2300000 | @brief Error code base. |
| OH_HTTP_UNSUPPORTED_PROTOCOL = (OH_HTTP_NETSTACK_E_BASE + 1) | @brief Unsupported protocol. |
| OH_HTTP_INVALID_URL = (OH_HTTP_NETSTACK_E_BASE + 3) | @brief Invalid URL format or missing URL. |
| OH_HTTP_RESOLVE_PROXY_FAILED = (OH_HTTP_NETSTACK_E_BASE + 5) | @brief Failed to resolve the proxy name. |
| OH_HTTP_RESOLVE_HOST_FAILED = (OH_HTTP_NETSTACK_E_BASE + 6) | @brief Failed to resolve the host name. |
| OH_HTTP_CONNECT_SERVER_FAILED = (OH_HTTP_NETSTACK_E_BASE + 7) | @brief Failed to connect to the server. |
| OH_HTTP_INVALID_SERVER_RESPONSE = (OH_HTTP_NETSTACK_E_BASE + 8) | @brief Invalid server response. |
| OH_HTTP_ACCESS_REMOTE_DENIED = (OH_HTTP_NETSTACK_E_BASE + 9) | @brief Access to the remote resource denied. |
| OH_HTTP_HTTP2_FRAMING_ERROR = (OH_HTTP_NETSTACK_E_BASE + 16) | @brief Error in the HTTP2 framing layer. |
| OH_HTTP_TRANSFER_PARTIAL_FILE = (OH_HTTP_NETSTACK_E_BASE + 18) | @brief Transferred a partial file. |
| OH_HTTP_WRITE_DATA_FAILED = (OH_HTTP_NETSTACK_E_BASE + 23) | @brief Failed to write the received data to the disk or application. |
| OH_HTTP_UPLOAD_FAILED = (OH_HTTP_NETSTACK_E_BASE + 25) | @brief Upload failed. |
| OH_HTTP_OPEN_LOCAL_DATA_FAILED = (OH_HTTP_NETSTACK_E_BASE + 26) | @brief Failed to open or read local data from the file or application. |
| OH_HTTP_OUT_OF_MEMORY = (OH_HTTP_NETSTACK_E_BASE + 27) | @brief Out of memory. |
| OH_HTTP_OPERATION_TIMEOUT = (OH_HTTP_NETSTACK_E_BASE + 28) | @brief Operation timeout. |
| OH_HTTP_TOO_MANY_REDIRECTIONS = (OH_HTTP_NETSTACK_E_BASE + 47) | @brief The number of redirections reaches the maximum allowed. |
| OH_HTTP_SERVER_RETURNED_NOTHING = (OH_HTTP_NETSTACK_E_BASE + 52) | @brief The server returned nothing (no header or data). |
| OH_HTTP_SEND_DATA_FAILED = (OH_HTTP_NETSTACK_E_BASE + 55) | @brief Failed to send data to the peer. |
| OH_HTTP_RECEIVE_DATA_FAILED = (OH_HTTP_NETSTACK_E_BASE + 56) | @brief Failed to receive data from the peer. |
| OH_HTTP_SSL_CERTIFICATE_ERROR = (OH_HTTP_NETSTACK_E_BASE + 58) | @brief Local SSL certificate error. |
| OH_HTTP_SSL_CIPHER_USED_ERROR = (OH_HTTP_NETSTACK_E_BASE + 59) | @brief The specified SSL cipher cannot be used. |
| OH_HTTP_INVALID_SSL_PEER_CERT = (OH_HTTP_NETSTACK_E_BASE + 60) | @brief Invalid SSL peer certificate or SSH remote key. |
| OH_HTTP_INVALID_ENCODING_FORMAT = (OH_HTTP_NETSTACK_E_BASE + 61) | @brief Invalid HTTP encoding format. |
| OH_HTTP_FILE_TOO_LARGE = (OH_HTTP_NETSTACK_E_BASE + 63) | @brief Maximum file size exceeded. |
| OH_HTTP_REMOTE_DISK_FULL = (OH_HTTP_NETSTACK_E_BASE + 70) | @brief Remote disk full. |
| OH_HTTP_REMOTE_FILE_EXISTS = (OH_HTTP_NETSTACK_E_BASE + 73) | @brief Remote file already exists. |
| OH_HTTP_SSL_CA_NOT_EXIST = (OH_HTTP_NETSTACK_E_BASE + 77) | @brief The SSL CA certificate does not exist or is inaccessible. |
| OH_HTTP_REMOTE_FILE_NOT_FOUND = (OH_HTTP_NETSTACK_E_BASE + 78) | @brief Remote file not found. |
| OH_HTTP_AUTHENTICATION_ERROR = (OH_HTTP_NETSTACK_E_BASE + 94) | @brief Authentication error. |
| OH_HTTP_REQUEST_INTERCEPTED = (OH_HTTP_NETSTACK_E_BASE + 996) | The request was intercepted by the HTTP global interceptor.<br>**Since**: 26.0.0 |
| OH_HTTP_ACCESS_DOMAIN_NOT_ALLOWED = (OH_HTTP_NETSTACK_E_BASE + 998) | @brief It is not allowed to access this domain. |
| OH_HTTP_UNKNOWN_ERROR = (OH_HTTP_NETSTACK_E_BASE + 999) | @brief Unknown error. |

### Http_ResponseCode

```c
enum Http_ResponseCode
```

**Description**

Defines http response code.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_HTTP_OK = 200 | @brief The request was successful. |
| OH_HTTP_CREATED = 201 | @brief Successfully requested and created a new resource. |
| OH_HTTP_ACCEPTED = 202 | @brief The request has been accepted but has not been processed completely. |
| OH_HTTP_NON_AUTHORITATIVE_INFO = 203 | @brief Unauthorized information. The request was successful. |
| OH_HTTP_NO_CONTENT = 204 | @brief No content. The server successfully processed, but did not return content. |
| OH_HTTP_RESET = 205 | @brief Reset the content. |
| OH_HTTP_PARTIAL = 206 | @brief Partial content. The server successfully processed some GET requests. |
| OH_HTTP_MULTI_CHOICE = 300 | @brief Multiple options. |
| OH_HTTP_MOVED_PERM = 301 | Permanently move. The requested resource has been permanently moved to a new URI, and the returned information will include the new URI. The browser will automatically redirect to the new URI. |
| OH_HTTP_MOVED_TEMP = 302 | @brief Temporary movement. |
| OH_HTTP_SEE_OTHER = 303 | @brief View other addresses. |
| OH_HTTP_NOT_MODIFIED = 304 | @brief Not modified. |
| OH_HTTP_USE_PROXY = 305 | @brief Using proxies. |
| OH_HTTP_BAD_REQUEST = 400 | @brief The server cannot understand the syntax error error requested by the client. |
| OH_HTTP_UNAUTHORIZED = 401 | @brief Request for user authentication. |
| OH_HTTP_PAYMENT_REQUIRED = 402 | @brief Reserved for future use. |
| OH_HTTP_FORBIDDEN = 403 | @brief The server understands the request from the requesting client, but refuses to execute it. |
| OH_HTTP_NOT_FOUND = 404 | @brief The server was unable to find resources (web pages) based on the client's request. |
| OH_HTTP_BAD_METHOD = 405 | @brief The method in the client request is prohibited. |
| OH_HTTP_NOT_ACCEPTABLE = 406 | @brief The server unabled to complete request based on the content characteristics requested by the client. |
| OH_HTTP_PROXY_AUTH = 407 | @brief Request authentication of the proxy's identity. |
| OH_HTTP_CLIENT_TIMEOUT = 408 | @brief The request took too long and timed out. |
| OH_HTTP_CONFLICT = 409 | The server may have returned this code when completing the client's PUT request, as there was a conflict when the server was processing the request. |
| OH_HTTP_GONE = 410 | @brief The resource requested by the client no longer exists. |
| OH_HTTP_LENGTH_REQUIRED = 411 | @brief The server is unable to process request information sent by the client without Content Length. |
| OH_HTTP_PRECON_FAILED = 412 | @brief The prerequisite for requesting information from the client is incorrect. |
| OH_HTTP_ENTITY_TOO_LARGE = 413 | @brief The request was rejected because the requested entity was too large for the server to process. |
| OH_HTTP_REQUEST_TOO_LONG = 414 | @brief The requested URI is too long (usually a URL) and the server cannot process it. |
| OH_HTTP_UNSUPPORTED_TYPE = 415 | @brief The server is unable to process the requested format. |
| OH_HTTP_RANGE_NOT_MET = 416 | @brief Requested Range not satisfiable. |
| OH_HTTP_INTERNAL_ERROR = 500 | @brief Internal server error, unable to complete the request. |
| OH_HTTP_NOT_IMPLEMENTED = 501 | @brief The server does not support the requested functionality and cannot complete the request. |
| OH_HTTP_BAD_GATEWAY = 502 | @brief The server acting as a gateway or proxy received an invalid request from the remote server. |
| OH_HTTP_UNAVAILABLE = 503 | @brief Due to overload or system maintenance, the server is temporarily unable to process client requests. |
| OH_HTTP_GATEWAY_TIMEOUT = 504 | @brief The server acting as gateway did not obtain requests from the remote server in a timely manner. |
| OH_HTTP_VERSION = 505 | @brief The version of the HTTP protocol requested by the server. |

### Http_AddressFamilyType

```c
enum Http_AddressFamilyType
```

**Description**

Defines the address Family.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

| Enum item | Description |
| -- | -- |
| HTTP_ADDRESS_FAMILY_DEFAULT = 0 | Default, The system automatically selects the IPv4 or IPv6 address of the domain name. |
| HTTP_ADDRESS_FAMILY_ONLY_V4 = 1 | IPv4, Selects the IPv4 address of the domain name. |
| HTTP_ADDRESS_FAMILY_ONLY_V6 = 2 | IPv6, Selects the IPv4 address of the domain name. |

### Http_HttpProtocol

```c
enum Http_HttpProtocol
```

**Description**

Defines the HTTP version.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_HTTP_NONE = 0 | Default choose by curl. |
| OH_HTTP1_1 | HTTP 1.1 version. |
| OH_HTTP2 | HTTP 2 version. |
| OH_HTTP3 | HTTP 3 version. |

### Http_CertType

```c
enum Http_CertType
```

**Description**

Defines the Cert Type.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_HTTP_PEM = 0 | PEM Cert Type. |
| OH_HTTP_DER = 1 | DER Cert Type. |
| OH_HTTP_P12 = 2 | P12 Cert Type. |

### Http_ProxyType

```c
enum Http_ProxyType
```

**Description**

Proxy type. Used to distinguish different proxy configurations.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

| Enum item | Description |
| -- | -- |
| HTTP_PROXY_NOT_USE | No proxy |
| HTTP_PROXY_SYSTEM | System proxy |
| HTTP_PROXY_CUSTOM | Use custom proxy |


## Function description

### Http_ResponseCallback()

```c
typedef void (*Http_ResponseCallback)(struct Http_Response *response, uint32_t errCode)
```

**Description**

Callback function that is invoked when response is received.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct Http_Response](capi-netstack-http-response.md) \*response | Http response struct, see [Http_Response](capi-netstack-http-response.md). |
| uint32_t errCode | Response error code. |

### Http_OnDataReceiveCallback()

```c
typedef void (*Http_OnDataReceiveCallback)(const char *data, size_t length)
```

**Description**

Callback function that is invoked when a response body is received.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char \*data | Response body. |
| size_t length | Length of response body. |

### Http_OnProgressCallback()

```c
typedef void (*Http_OnProgressCallback)(uint64_t totalSize, uint64_t transferredSize)
```

**Description**

Callback function invoked during request/response data transmission.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t totalSize | total size. |
| uint64_t transferredSize | transferred size. |

### Http_OnHeaderReceiveCallback()

```c
typedef void (*Http_OnHeaderReceiveCallback)(Http_Headers *headers)
```

**Description**

Callback called when header are received.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Http_Headers](capi-netstack-http-headers.md) \*headers | Headers of the received requests, which points to the pointer of [Http_Headers](capi-netstack-http-headers.md). |

### Http_OnVoidCallback()

```c
typedef void (*Http_OnVoidCallback)(void)
```

**Description**

Empty callback function for requested DataEnd or Canceled event callback.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20


