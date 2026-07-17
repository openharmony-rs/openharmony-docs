# Http_RequestOptions

```c
typedef struct Http_RequestOptions {...} Http_RequestOptions
```

## 概述

定义HTTP请求配置的结构体。

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *method | HTTP请求方法。 |
| uint32_t priority | HTTP请求优先级。 |
| [Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to the HTTP request header. For details, see [Http_Headers](capi-netstack-http-headers.md). |
| uint32_t readTimeout | 读取超时时间。 |
| uint32_t connectTimeout | 连接超时时间。 |
| [Http_HttpProtocol](capi-net-http-type-h.md#http_httpprotocol) httpProtocol | HTTP protocol. For details, see [Http_HttpProtocol](capi-net-http-type-h.md#http_httpprotocol). |
| [Http_Proxy](capi-netstack-http-proxy.md) *httpProxy | Pointer to the HTTP proxy configuration, which indicates whether to use a proxy. By default, proxy is not used.For details, see [Http_Proxy](capi-netstack-http-proxy.md). |
| const char *caPath | 证书路径，如果设置了此参数，系统将使用用户指定路径的CA证书（开发者需保证该路径下CA证书的可访问性），否则将使用系统预设CA证书。 |
| int64_t resumeFrom | 用于设置下载起始位置，该参数只能用于GET方法，不要用于其他。 |
| int64_t resumeTo | 用于设置下载结束位置，该参数只能用于GET方法，不要用于其他。 |
| [Http_ClientCert](capi-netstack-http-clientcert.md) *clientCert | Pointer to the client certificate configuration. For details, see [Http_ClientCert](capi-netstack-http-clientcert.md). |
| const char *dnsOverHttps | 设置使用HTTPS协议的服务器进行DNS解析。 |
| [Http_AddressFamilyType](capi-net-http-type-h.md#http_addressfamilytype) addressFamily | IP address family. For details, see [Http_AddressFamilyType](capi-net-http-type-h.md#http_addressfamilytype). |


