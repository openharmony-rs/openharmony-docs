# net_ssl_c_type.h

## 概述

定义SSL/TLS证书链校验模块的C接口需要的数据结构。

**库：** libnet_ssl.so

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**相关模块：** [netstack](capi-network-kit-netstack.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [NetStack_CertBlob](capi-netstack-netstack-certblob.md) | - | Defines the certificate data structure. |
| [NetStack_CertificatePinning](capi-netstack-netstack-certificatepinning.md) | NetStack_CertificatePinning | Defines certificate pinning information. |
| [NetStack_Certificates](capi-netstack-netstack-certificates.md) | NetStack_Certificates | Define certificate information. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [NetStack_CertType](#netstack_certtype) | - | Certificate type enums. |
| [NetStack_CertificatePinningKind](#netstack_certificatepinningkind) | NetStack_CertificatePinningKind | Certificate pinning type enums. |
| [NetStack_HashAlgorithm](#netstack_hashalgorithm) | NetStack_HashAlgorithm | Hash algorithm enums. |

## 枚举类型说明

### NetStack_CertType

```c
enum NetStack_CertType
```

**描述：**

Certificate type enums.

<!--Device-enum NetStack_CertType--><!--Device-enum NetStack_CertType-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| NETSTACK_CERT_TYPE_PEM = 0 | PEM certificate.<br><!--Device-NETSTACK_CERT_TYPE_PEM = 0--><!--Device-NETSTACK_CERT_TYPE_PEM = 0-End--> |
| NETSTACK_CERT_TYPE_DER = 1 | DER certificate.<br><!--Device-NETSTACK_CERT_TYPE_DER = 1--><!--Device-NETSTACK_CERT_TYPE_DER = 1-End--> |
| NETSTACK_CERT_TYPE_INVALID | Invalid certificate.<br><!--Device-NETSTACK_CERT_TYPE_INVALID--><!--Device-NETSTACK_CERT_TYPE_INVALID-End--> |

### NetStack_CertificatePinningKind

```c
enum NetStack_CertificatePinningKind
```

**描述：**

Certificate pinning type enums.

<!--Device-enum NetStack_CertificatePinningKind--><!--Device-enum NetStack_CertificatePinningKind-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| PUBLIC_KEY | Public key lock type.<br><!--Device-PUBLIC_KEY--><!--Device-PUBLIC_KEY-End--> |

### NetStack_HashAlgorithm

```c
enum NetStack_HashAlgorithm
```

**描述：**

Hash algorithm enums.

<!--Device-enum NetStack_HashAlgorithm--><!--Device-enum NetStack_HashAlgorithm-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| SHA_256 | Sha256<br><!--Device-SHA_256--><!--Device-SHA_256-End--> |


