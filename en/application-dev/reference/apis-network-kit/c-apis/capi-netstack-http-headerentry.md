# Http_HeaderEntry

```c
struct Http_HeaderEntry {...}
```

## Overview

Defines all key-value pairs in the request or response header.

<!--Device-struct Http_HeaderEntry {...}--><!--Device-struct Http_HeaderEntry {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *key | Key in the request or response header. |
| Http_HeaderValue *value | Value of the key in the request or response header. For details, see [Http_HeaderValue](capi-netstack-http-headervalue.md). |
| struct Http_HeaderEntry *next | Pointer to Pointer to the next **Http_HeaderEntry**. |


