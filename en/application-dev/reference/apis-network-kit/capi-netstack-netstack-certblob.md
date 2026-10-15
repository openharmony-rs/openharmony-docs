# NetStack_CertBlob

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=78a295bda0d44cf639349e39d2243d7a5a53a568 translatedAt=2026-09-28T01:13:49.548Z pushedAt=2026-10-09T01:44:41.563Z -->

```c
struct NetStack_CertBlob {...}
```

## Overview

Defines the certificate data structure.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_ssl_c_type.h](capi-net-ssl-c-type-h.md)

## Summary

### Member Variables

| Name                                                                       | Description|
|---------------------------------------------------------------------------| -- |
| enum [NetStack_CertType](capi-net-ssl-c-type-h.md#netstack_certtype) type | Certificate type.|
| uint32_t size                                                             | Length of the certificate content. Unit: Byte. |
| uint8_t *data                                                             | Certificate data.|
