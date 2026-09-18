# peration_ae_init

```c
struct peration_ae_init {...}
```

## Overview

Defines the AE initialization data.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *nonce | nonce |
| size_t nonce_len | Leng of nonce |
| uint32_t tag_len | Length of the tag |
| size_t aad_len | Length of the additional authenticated data (AAD) |
| size_t payload_len | Length of the payload |


