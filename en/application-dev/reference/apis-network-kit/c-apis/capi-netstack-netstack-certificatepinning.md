# NetStack_CertificatePinning

```c
typedef struct NetStack_CertificatePinning {...} NetStack_CertificatePinning
```

## Overview

Defines certificate pinning information.

<!--Device-struct NetStack_CertificatePinning {...}--><!--Device-struct NetStack_CertificatePinning {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 12

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [NetStack_CertificatePinningKind](capi-net-ssl-c-type-h.md#netstack_certificatepinningkind) kind | Certificate lock type<br><!--Device-NetStack_CertificatePinningKind kind--><!--Device-NetStack_CertificatePinningKind kind-End--> |
| [NetStack_HashAlgorithm](capi-net-ssl-c-type-h.md#netstack_hashalgorithm) hashAlgorithm | Hash algorithm<br><!--Device-NetStack_HashAlgorithm hashAlgorithm--><!--Device-NetStack_HashAlgorithm hashAlgorithm-End--> |
| *publicKeyHash | <!--Device-*publicKeyHash--><!--Device-*publicKeyHash-End--> |


