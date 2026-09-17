# peration_src_dest

```c
struct peration_src_dest {...}
```

## Overview

Defines a structure to hold the input and output data.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *src_data | Source data |
| size_t src_len | Length of the source data |
| void *dest_data | Destination data |
| size_t *dest_len | Length of the destination data |


