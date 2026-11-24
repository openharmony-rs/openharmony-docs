# Http_RequestOptions

```c
typedef struct Http_RequestOptions {...} Http_RequestOptions
```

## Overview

Defines the structure of HTTP requests.

<!--Device-struct Http_RequestOptions {...}--><!--Device-struct Http_RequestOptions {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *method | HTTP request method.<br><!--Device-const char *method--><!--Device-const char *method-End--> |
| uint32_t priority | HTTP request priority.<br><!--Device-uint32_t priority--><!--Device-uint32_t priority-End--> |
| [Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to the HTTP request header. For details, see [Http_Headers](capi-netstack-http-headers.md).<br><!--Device-Http_Headers *headers--><!--Device-Http_Headers *headers-End--> |
| uint32_t readTimeout | Read timeout duration.<br><!--Device-uint32_t readTimeout--><!--Device-uint32_t readTimeout-End--> |
| uint32_t connectTimeout | Connection timeout duration.<br><!--Device-uint32_t connectTimeout--><!--Device-uint32_t connectTimeout-End--> |
| [Http_HttpProtocol](capi-net-http-type-h.md#http_httpprotocol) httpProtocol | HTTP protocol. For details, see [Http_HttpProtocol](capi-net-http-type-h.md#http_httpprotocol).<br><!--Device-Http_HttpProtocol httpProtocol--><!--Device-Http_HttpProtocol httpProtocol-End--> |
| [Http_Proxy](capi-netstack-http-proxy.md) *httpProxy | Pointer to the HTTP proxy configuration, which indicates whether to use a proxy. By default, proxy is not used. For details, see [Http_Proxy](capi-netstack-http-proxy.md).<br><!--Device-Http_Proxy *httpProxy--><!--Device-Http_Proxy *httpProxy-End--> |
| const char *caPath | Certificate path. If the CA certificate path is set, the system uses the CA certificate in the specified path. Otherwise, the system uses the preset CA certificate.<br><!--Device-const char *caPath--><!--Device-const char *caPath-End--> |
| int64_t resumeFrom | Download start position. This field can be used only for the GET method.<br><!--Device-int64_t resumeFrom--><!--Device-int64_t resumeFrom-End--> |
| int64_t resumeTo | Download end position. This field can be used only for the GET method.<br><!--Device-int64_t resumeTo--><!--Device-int64_t resumeTo-End--> |
| [Http_ClientCert](capi-netstack-http-clientcert.md) *clientCert | Pointer to the client certificate configuration. For details, see [Http_ClientCert](capi-netstack-http-clientcert.md).<br><!--Device-Http_ClientCert *clientCert--><!--Device-Http_ClientCert *clientCert-End--> |
| const char *dnsOverHttps | HTTPS server for DNS resolution.<br><!--Device-const char *dnsOverHttps--><!--Device-const char *dnsOverHttps-End--> |
| [Http_AddressFamilyType](capi-net-http-type-h.md#http_addressfamilytype) addressFamily | IP address family. For details, see [Http_AddressFamilyType](capi-net-http-type-h.md#http_addressfamilytype).<br><!--Device-Http_AddressFamilyType addressFamily--><!--Device-Http_AddressFamilyType addressFamily-End--> |


