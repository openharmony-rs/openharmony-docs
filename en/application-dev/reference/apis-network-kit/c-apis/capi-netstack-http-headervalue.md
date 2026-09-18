# Http_HeaderValue

```c
typedef struct Http_HeaderValue {...} Http_HeaderValue
```

## Overview

Defines the type of a mapped value in a request or response header.

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *value | Value of a key-value pair in the header. |
| struct [Http_HeaderValue](capi-netstack-http-headervalue.md) *next | Pointer to Pointer to the next **Http_HeaderValue**. |


