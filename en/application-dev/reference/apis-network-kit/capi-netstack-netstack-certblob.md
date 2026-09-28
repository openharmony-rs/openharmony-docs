# NetStack_CertBlob

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T01:31:39.830Z pushedAt=2026-09-24T06:00:14.125Z -->

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
| [NetStack_CertType](capi-net-ssl-c-type-h.md#netstack_certtype) type | Certificate type. |
| uint32_t size                                                             | Certificate content length.|
| uint8_t *data                                                             | Certificate data.|
