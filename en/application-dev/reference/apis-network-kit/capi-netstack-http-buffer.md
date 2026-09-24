# Http_Buffer
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=717c394d6f6b10e0c1525acb86c2aa05a1665e70 translatedAt=2026-09-28T01:12:07.036Z pushedAt=2026-10-09T01:40:06.393Z -->

```c
typedef struct Http_Buffer {...} Http_Buffer
```

## Overview

Defines the HTTP buffer structure.

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char *buffer | Buffer data. |
| uint32_t length | Buffer length. Unit: Byte. |


