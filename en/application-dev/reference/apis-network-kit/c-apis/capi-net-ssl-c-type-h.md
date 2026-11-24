# net_ssl_c_type.h

## Overview

Defines the data structures for the C APIs of the SSL/TLS certificate chain verification module.

**Library**: libnet_ssl.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NetStack_CertBlob](capi-netstack-netstack-certblob.md) | - | Defines the certificate data structure. |
| [NetStack_CertificatePinning](capi-netstack-netstack-certificatepinning.md) | NetStack_CertificatePinning | Defines certificate pinning information. |
| [NetStack_Certificates](capi-netstack-netstack-certificates.md) | NetStack_Certificates | Define certificate information. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NetStack_CertType](#netstack_certtype) | - | Certificate type enums. |
| [NetStack_CertificatePinningKind](#netstack_certificatepinningkind) | NetStack_CertificatePinningKind | Certificate pinning type enums. |
| [NetStack_HashAlgorithm](#netstack_hashalgorithm) | NetStack_HashAlgorithm | Hash algorithm enums. |

## Enum type description

### NetStack_CertType

```c
enum NetStack_CertType
```

**Description**

Certificate type enums.

<!--Device-enum NetStack_CertType--><!--Device-enum NetStack_CertType-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

| Enum item | Description |
| -- | -- |
| NETSTACK_CERT_TYPE_PEM = 0 | PEM certificate.<br><!--Device-NETSTACK_CERT_TYPE_PEM = 0--><!--Device-NETSTACK_CERT_TYPE_PEM = 0-End--> |
| NETSTACK_CERT_TYPE_DER = 1 | DER certificate.<br><!--Device-NETSTACK_CERT_TYPE_DER = 1--><!--Device-NETSTACK_CERT_TYPE_DER = 1-End--> |
| NETSTACK_CERT_TYPE_INVALID | Invalid certificate.<br><!--Device-NETSTACK_CERT_TYPE_INVALID--><!--Device-NETSTACK_CERT_TYPE_INVALID-End--> |

### NetStack_CertificatePinningKind

```c
enum NetStack_CertificatePinningKind
```

**Description**

Certificate pinning type enums.

<!--Device-enum NetStack_CertificatePinningKind--><!--Device-enum NetStack_CertificatePinningKind-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12

| Enum item | Description |
| -- | -- |
| PUBLIC_KEY | Public key lock type.<br><!--Device-PUBLIC_KEY--><!--Device-PUBLIC_KEY-End--> |

### NetStack_HashAlgorithm

```c
enum NetStack_HashAlgorithm
```

**Description**

Hash algorithm enums.

<!--Device-enum NetStack_HashAlgorithm--><!--Device-enum NetStack_HashAlgorithm-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12

| Enum item | Description |
| -- | -- |
| SHA_256 | Sha256<br><!--Device-SHA_256--><!--Device-SHA_256-End--> |


