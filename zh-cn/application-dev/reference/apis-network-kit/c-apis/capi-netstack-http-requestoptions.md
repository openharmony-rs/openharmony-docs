# Http_RequestOptions

```c
typedef struct Http_RequestOptions {...} Http_RequestOptions
```

## 概述

定义HTTP请求配置的结构体。

<!--Device-struct Http_RequestOptions {...}--><!--Device-struct Http_RequestOptions {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *method | HTTP请求方法。<br><!--Device-const char *method--><!--Device-const char *method-End--> |
| uint32_t priority | HTTP请求优先级。<br><!--Device-uint32_t priority--><!--Device-uint32_t priority-End--> |
| [Http_Headers](capi-netstack-http-headers.md) *headers | HTTP请求头，指向Http_Headers的指针，参考[Http_Headers](capi-netstack-http-headers.md)。<br><!--Device-Http_Headers *headers--><!--Device-Http_Headers *headers-End--> |
| uint32_t readTimeout | 读取超时时间。<br><!--Device-uint32_t readTimeout--><!--Device-uint32_t readTimeout-End--> |
| uint32_t connectTimeout | 连接超时时间。<br><!--Device-uint32_t connectTimeout--><!--Device-uint32_t connectTimeout-End--> |
| [Http_HttpProtocol](capi-net-http-type-h.md#http_httpprotocol) httpProtocol | 使用的协议，参考[Http_HttpProtocol](capi-net-http-type-h.md#http_httpprotocol)。<br><!--Device-Http_HttpProtocol httpProtocol--><!--Device-Http_HttpProtocol httpProtocol-End--> |
| [Http_Proxy](capi-netstack-http-proxy.md) *httpProxy | 代理配置信息，表示是否使用代理，默认不使用代理，参考[Http_Proxy](capi-netstack-http-proxy.md)。<br><!--Device-Http_Proxy *httpProxy--><!--Device-Http_Proxy *httpProxy-End--> |
| const char *caPath | 证书路径，如果设置了此参数，系统将使用用户指定路径的CA证书（开发者需保证该路径下CA证书的可访问性），否则将使用系统预设CA证书。<br><!--Device-const char *caPath--><!--Device-const char *caPath-End--> |
| int64_t resumeFrom | 用于设置下载起始位置，该参数只能用于GET方法，不要用于其他。<br><!--Device-int64_t resumeFrom--><!--Device-int64_t resumeFrom-End--> |
| int64_t resumeTo | 用于设置下载结束位置，该参数只能用于GET方法，不要用于其他。<br><!--Device-int64_t resumeTo--><!--Device-int64_t resumeTo-End--> |
| [Http_ClientCert](capi-netstack-http-clientcert.md) *clientCert | 传输客户端证书配置信息，参考[Http_ClientCert](capi-netstack-http-clientcert.md)。<br><!--Device-Http_ClientCert *clientCert--><!--Device-Http_ClientCert *clientCert-End--> |
| const char *dnsOverHttps | 设置使用HTTPS协议的服务器进行DNS解析。<br><!--Device-const char *dnsOverHttps--><!--Device-const char *dnsOverHttps-End--> |
| [Http_AddressFamilyType](capi-net-http-type-h.md#http_addressfamilytype) addressFamily | 支持解析目标域名时限定地址类型，参考[Http_AddressFamilyType](capi-net-http-type-h.md#http_addressfamilytype)。<br><!--Device-Http_AddressFamilyType addressFamily--><!--Device-Http_AddressFamilyType addressFamily-End--> |


