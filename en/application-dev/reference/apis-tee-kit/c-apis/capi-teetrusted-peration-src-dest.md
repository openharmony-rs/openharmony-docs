# peration_src_dest

```c
typedef struct peration_src_dest {...} operation_src_dest
```

## Overview

Defines a structure to hold the input and output data.

<!--Device-struct peration_src_dest {...}--><!--Device-struct peration_src_dest {...}-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *src_data | Source data<br><!--Device-void *src_data--><!--Device-void *src_data-End--> |
| size_t src_len | Length of the source data<br><!--Device-size_t src_len--><!--Device-size_t src_len-End--> |
| void *dest_data | Destination data<br><!--Device-void *dest_data--><!--Device-void *dest_data-End--> |
| size_t *dest_len | Length of the destination data<br><!--Device-size_t *dest_len--><!--Device-size_t *dest_len-End--> |


