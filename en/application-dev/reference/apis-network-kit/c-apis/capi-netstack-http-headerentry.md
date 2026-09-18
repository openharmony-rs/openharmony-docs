# Http_HeaderEntry

```c
typedef struct Http_HeaderEntry {...} Http_HeaderEntry
```

## Overview

Defines all key-value pairs in the request or response header.

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *key | Key in the request or response header. |
| [Http_HeaderValue](capi-netstack-http-headervalue.md) *value | Value of the key in the request or response header. For details, see [Http_HeaderValue](capi-netstack-http-headervalue.md). |
| struct [Http_HeaderEntry](capi-netstack-http-headerentry.md) *next | Pointer to Pointer to the next **Http_HeaderEntry**. |


