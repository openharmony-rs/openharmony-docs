# Http_ClientCert

```c
typedef struct Http_ClientCert {...} Http_ClientCert
```

## 概述

发送到服务端的客户端证书配置，服务端将通过客户端证书校验客户端身份。

<!--Device-struct Http_ClientCert {...}--><!--Device-struct Http_ClientCert {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *certPath | 证书路径。<br><!--Device-char *certPath--><!--Device-char *certPath-End--> |
| [Http_CertType](capi-net-http-type-h.md#http_certtype) type | 证书类型，默认是PEM，参考[Http_CertType](capi-net-http-type-h.md#http_certtype)。<br><!--Device-Http_CertType type--><!--Device-Http_CertType type-End--> |
| char *keyPath | 证书密钥的路径。<br><!--Device-char *keyPath--><!--Device-char *keyPath-End--> |
| char *keyPassword | 证书密钥的密码。<br><!--Device-char *keyPassword--><!--Device-char *keyPassword-End--> |


