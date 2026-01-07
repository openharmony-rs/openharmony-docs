# NetStack_CertificatePinning

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct NetStack_CertificatePinning {...} NetStack_CertificatePinning
```

## Overview

Defines certificate pinning information.

**Since**: 12

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## Summary

### Member Variables

| Name                                                                                              | Description|
|--------------------------------------------------------------------------------------------------| -- |
| [NetStack_CertificatePinningKind](capi-net-ssl-c-type-h.md#netstack_certificatepinningkind) kind | Certificate lock type.|
| [NetStack_HashAlgorithm](capi-net-ssl-c-type-h.md#netstack_hashalgorithm) hashAlgorithm          | Hash algorithm.|
| char *publicKeyHash                                                                              | Hash value.|
